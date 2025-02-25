# Search Engine using Apache Nutch

## Overview
This project focuses on developing a **search engine** using **Apache Nutch** and **Apache Tomcat**. The goal is to build a web crawler capable of indexing web content from various sources and providing efficient search results to users.

## Objectives
- Configure and deploy a functional search engine.
- Crawl and index web pages using **Apache Nutch**.
- Serve the indexed data using **Apache Tomcat**.
- Demonstrate the feasibility of building a custom search engine.

## Tools Used
- **Operating System**: macOS Sonoma 14.1 (Unix-based)
- **Apache Nutch**: v0.9
- **Apache Tomcat**: v9.0.82
- **Java**: v21.0.1

## Setup and Installation
### 1. Install and Configure Apache Tomcat
Apache Tomcat is required to browse the crawled data. Steps:
1. Download and extract **Apache Tomcat 9.0.82**.
2. Set up the `JAVA_HOME` environment variable.
3. Start the Tomcat server:
   ```bash
   /Users/krishna/Downloads/apache-tomcat-9.0.82/bin/startup.sh
   ```

### 2. Install and Configure Apache Nutch
Apache Nutch is an open-source web crawler used for indexing web pages.
1. Download and extract **Apache Nutch 0.9**.
2. Navigate to the extracted folder:
   ```bash
   cd /Users/krishna/Downloads/nutch-0.9
   ```
3. Create a directory `urls` inside `nutch-0.9/bin` and add a `seed.txt` file with URLs to crawl (e.g., `http://www.nits.ac.in`).

### 3. Modify Configuration Files
Edit the following files inside `/conf`:
- **crawl-urlfilter.txt**:
  ```
  +^http://([a-z0-9]*\.)*www.nits.ac.in/
  ```
- **regex-urlfilter.txt**:
  ```
  +^http://([a-z0-9]*\.)*www.nits.ac.in
  ```
- **nutch-site.xml**:
  ```xml
  <property>
      <name>http.agent.name</name>
      <value>My Nutch Spider</value>
  </property>
  ```

### 4. Start Crawling
Run the following command to begin crawling:
```bash
./nutch crawl urls -dir Crawled_Data -depth 3 -topN 50
```
- `Crawled_Data`: Stores the crawled data.
- `-depth 3`: Defines the depth of the crawl.
- `-topN 50`: Limits the number of pages to be crawled.

### 5. Deploy Nutch on Apache Tomcat
1. Copy `nutch-0.9.war` to `apache-tomcat-9.0.82/webapps/`.
2. Modify `search.dir` in `nutch-site.xml` to point to the crawled data directory.
3. Start the Tomcat server and open a browser to access:
   ```
   http://localhost:8080/nutch-0.9/
   ```
4. Enter a search query and view the results.

## Results
After executing all steps successfully:
- The Apache Nutch search engine homepage appears.
- Entering search queries returns indexed results from the crawled data.
- A search query like **“m.tech”** produced 61 results.

## Repository
All files and configurations are uploaded to GitHub:  
🔗 [GitHub Repository](https://github.com/mohanreddy91/search_engine)

## Conclusion
This project successfully demonstrates:
- Configuration of **Apache Nutch** and **Tomcat**.
- Crawling and indexing of web pages.
- Challenges like managing web diversity and optimizing crawl performance were tackled effectively.

## References
1. [Apache Nutch Tutorial](https://cwiki.apache.org/confluence/display/NUTCH/NutchTutorial)
2. [Nutch Installation Guide](https://nutchinstall.blogspot.com/2007/07/setting-up-cygwin-and-nutch.html)
3. [YouTube Guide](https://youtube.com/playlist?list=PL_RrEj88onS_-T5zBnkkm07suqQtCLFpT)

🚀 *This project serves as a foundation for building more advanced search engines using open-source technologies.*

