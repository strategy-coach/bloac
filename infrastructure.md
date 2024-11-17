# Business Lifecycles and Operations as Code (BLOaC) Infrastructure

While the **Business Lifecycles as Code (BLOaC)** framework provides unparalleled transparency, automation, and collaboration, its reliance on GitOps principles, repositories, and Markdown-based content creation can pose challenges for non-technical staff, such as:

1. **Unfamiliarity with Git and Repositories**:
   - Non-technical staff may not have experience with tools like GitHub, GitLab, or BitBucket.

2. **Markdown and Frontmatter Complexity**:
   - Using structured formats like Markdown with frontmatter for content might feel technical or unintuitive.

3. **Navigation and Workflow Complexity**:
   - Navigating repositories, issues, and pull requests can feel overwhelming compared to traditional tools like CRMs or project management platforms.

The key to overcoming these challenges lies in treating the **GitOps-based infrastructure** as the backend foundation and building **user-friendly Web UIs and applications** on top of it. These overlays provide intuitive interfaces for non-technical users while retaining the flexibility, scalability, and automation benefits of BLOaC.

## BLOaC GitOps is Infrastructure, not UI/UX

In this model, GitOps tools like repositories, Markdown content, and GitHub Projects are treated as **backend infrastructure** for managing business lifecycles. The infrastructure acts as:

- **A Single Source of Truth**: Ensuring that all content, tasks, and processes are version-controlled and auditable.
- **Scalable and Flexible Foundation**: Supporting both technical and non-technical workflows.
- **Integration Hub**: Seamlessly connecting with other tools and APIs for automation.

By decoupling the infrastructure from the user interface, organizations can focus on maintaining the benefits of GitOps while addressing usability concerns.

## User-Friendly Overlays

To make BLOaC accessible for non-technical staff, **user-friendly overlays** can be layered on top of the GitOps infrastructure. These overlays include:

### **Web-Based UIs**
- **What They Do**:
  - Abstract the complexity of repositories, Markdown, and Git workflows.
  - Provide intuitive interfaces for creating, editing, and managing content and tasks.
- **Examples**:
  - **Netlify CMS**: A headless CMS that uses Git as the backend but provides a user-friendly UI for content creation.
  - **Prose.io**: A simple Markdown editor integrated with GitHub.
  - Custom-built dashboards tailored to specific business lifecycles.

### **Task Management Tools**
- **What They Do**:
  - Offer Kanban boards or task lists that sync directly with GitHub Issues or Projects.
- **Examples**:
  - **ZenHub**: A project management tool that overlays GitHub Projects.
  - **Linear**: Syncs with GitHub to offer a polished task management experience.

### **WYSIWYG Editors**
- **What They Do**:
  - Allow users to edit Markdown content in a "What You See Is What You Get" (WYSIWYG) interface, hiding the complexity of Markdown syntax.
- **Examples**:
  - **StackEdit**: A Markdown editor with WYSIWYG features.
  - Custom in-house editors.

### **Automated Git Workflows**
- **What They Do**:
  - Automate common Git workflows like pull requests, commits, and merges.
- **Examples**:
  - **GitHub Actions**: Automates repetitive tasks like generating reports, notifying stakeholders, or merging updates.
  - **CI/CD Integrations**: Handle updates and deployments without manual Git commands.

### Benefits of GitOps as Infrastructure with Ease of Use Overlays as UIs

#### For Non-Technical Users
- **Ease of Use**:
  - Users interact with familiar UI elements like forms, dashboards, and drag-and-drop interfaces.
- **Seamless Integration**:
  - Changes made through the UI automatically sync with the GitOps backend, ensuring consistency.

#### **For Organizations**
- **Maintains Flexibility**:
  - The underlying infrastructure remains adaptable to changes in business processes.
- **Preserves Transparency and Auditability**:
  - All actions in the UI are recorded in the repository, ensuring full traceability.
- **Scales Across Teams**:
  - Different overlays can be tailored for marketing, sales, support, and other teams while sharing the same backend.

## Real-World Example: Sales Lifecycle in BLOaC

### Backend Infrastructure
- Leads and tasks are stored as Markdown files with frontmatter in a GitHub repository.
- GitHub Issues are used to track tasks and progress.

### Web-Based Overlay
- A Web UI allows sales reps to:
  - Enter new leads through forms.
  - Drag and drop tasks across pipeline stages (e.g., Lead → Proposal → Closing).
  - View reports and metrics in real-time dashboards.

### Automation
- GitHub Actions notify sales reps about follow-ups or deal deadlines.
- CI/CD workflows generate weekly sales performance reports.

## **Addressing Analytics and Querying Challenges in BLaaC with GitOps Infrastructure**

### Challenges in Analytics and Querying with GitOps

While using GitOps infrastructure (repositories, Markdown, GitHub Issues) for managing business lifecycles provides transparency, automation, and flexibility, it does introduce challenges when it comes to analytics and querying, including:

1. **Decentralized Content**:
   - Business data is spread across Markdown files, Issues, and repository metadata, making aggregation complex.

2. **Unstructured Formats**:
   - While Markdown and frontmatter provide some structure, they are not inherently designed for relational querying.

3. **Performance and Scale**:
   - Analyzing large datasets across multiple repositories requires manual extraction or custom scripts, which can be inefficient.

4. **Cross-Repository Reporting**:
   - Combining data from multiple repositories for unified analysis can be cumbersome.

### Solution: Leveraging Tools like `surveilr`

[`surveilr`](https://www.surveilr.com) solves these challenges by ingesting diverse content sources (e.g., Markdown files, GitHub Issues, metadata) into a **uniform SQL schema**, enabling powerful querying and analytics capabilities. By integrating with GitOps infrastructure, `surveilr` acts as a bridge between unstructured Git content and structured data systems.

#### **How `surveilr` Works**

1. **Ingestion**:
   - `surveilr` pulls data from:
     - Markdown files with frontmatter.
     - GitHub Issues, Projects, and Discussions.
     - Repository metadata (e.g., commit history, tags).
   - These sources are standardized into a SQL database schema.

2. **SQL Schema for Business Lifecycles**:
   - Data is stored in a structured format, with tables for:
     - **Tasks**: Representing Issues, pull requests, and to-dos.
     - **Content**: Markdown files with parsed frontmatter.
     - **Metadata**: Commit history, authorship, and timestamps.

3. **Querying and Analytics**:
   - Teams can write SQL queries to:
     - Generate pipeline metrics (e.g., deal conversion rates, customer health scores).
     - Track activity timelines and trends.
     - Build cross-repository reports on project or lifecycle progress.

4. **Automation**:
   - GitHub Actions or other CI/CD tools can trigger `surveilr` processes to:
     - Regularly update the SQL database with the latest Git content.
     - Automatically generate dashboards or export data to BI tools.

#### **Example Workflow with `surveilr`**

##### **1. Infrastructure Setup**
- Use Git repositories for BLaaC infrastructure.
- Store lifecycle data (e.g., leads, customer success metrics) in Markdown files with frontmatter.

##### **2. Ingestion**
- Configure `surveilr` to sync data from:
  - Markdown files in `sales-pipeline/` and `customer-success/` repositories.
  - GitHub Issues labeled as "Feedback" or "Tasks."
  - Repository metadata for tracking contributor activity.

##### **3. SQL Database**
- (TODO: update this to match RSSD structures) `surveilr` ingests the data into `uniform_resource` table rows like:
  ```
  sales_pipeline
  ├── id
  ├── name
  ├── stage
  ├── value
  ├── owner
  ├── last_updated

  issues
  ├── id
  ├── title
  ├── status
  ├── repository
  ├── labels
  ├── created_at
  ├── updated_at
  ```

##### **4. Query and Analyze**
- Run SQL queries to:
  - Identify deals stuck in the pipeline.
  - Aggregate customer health scores across repositories.
  - Measure team performance by tracking task completion rates.

##### **5. Automation**
- Use GitHub Actions to:
  - Trigger `surveilr` ingestion after every commit or Issue update.
  - Generate SQL reports automatically and store them in a `reports/` repository.
  - Send notifications or summaries to Slack, email, or dashboards.

### **Benefits of Combining GitOps with `surveilr`**

#### **For Non-Technical Users**
- **Simplified Access**:
  - SQL databases provide a familiar querying format for analysts.
  - Dashboards built on top of the SQL schema eliminate the need to navigate Git repositories.

#### **For Technical Teams**
- **Unified Data Layer**:
  - Data from multiple repositories and formats is centralized in one place for analysis.
- **Maintain Flexibility**:
  - The GitOps infrastructure remains intact, while `surveilr` handles data translation.

#### **For Organizations**
- **Scalable Analytics**:
  - Easily run cross-lifecycle reports without modifying the GitOps setup.
- **Enhanced Automation**:
  - Automate ingestion and analysis workflows to keep data up-to-date.

### **Example Use Cases**

#### **1. Sales Metrics**
- **Problem**: Sales teams want to analyze win rates by pipeline stage.
- **Solution**:
  - `surveilr` ingests pipeline data from Markdown files.
  - Query the SQL schema:
    ```sql
    SELECT stage, COUNT(*) AS deals, SUM(value) AS total_value
    FROM sales_pipeline
    GROUP BY stage;
    ```

#### **2. Customer Success Insights**
- **Problem**: Customer success teams need to monitor health scores and churn risks.
- **Solution**:
  - `surveilr` ingests health score metrics and customer feedback.
  - Build a dashboard showing trends and at-risk accounts.

#### **3. Team Productivity**
- **Problem**: Managers want to track task completion rates across repositories.
- **Solution**:
  - Query tasks from the `issues` table to generate completion metrics.

### Learn More

While GitOps infrastructure provides enormous benefits in transparency, automation, and flexibility, it can make querying and analytics more complex. Tools like **`surveilr`** bridge this gap by ingesting Git content into a **structured SQL database**, enabling easy querying and powerful analytics. This combination:

- **Preserves the GitOps Foundation**: Ensuring flexibility and scalability.
- **Simplifies Analytics**: Making lifecycle data accessible to analysts and non-technical users.
- **Automates Insights**: Streamlining data extraction and report generation with CI/CD tools.

By adopting tools like `surveilr`, organizations can unlock the full potential of **Business Lifecycles as Code**, ensuring all teams—from technical to non-technical—can benefit from a unified, data-driven approach to business operations.
