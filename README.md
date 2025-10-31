[![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat)](LICENCE)

<a name="top"></a>

# ToolsForMCPServer-extension (ToolsForMCPServer as Gemini Extension)

The name of this MCP server is `tools-for-mcp-server-extension`. The base MCP server is from [https://github.com/tanaikech/ToolsForMCPServer](https://github.com/tanaikech/ToolsForMCPServer).

<a name="abstract"></a>

# Description

The Gemini CLI is continually advancing, and Gemini CLI extensions have recently been released. [Ref](https://cloud.google.com/blog/products/databases/gemini-cli-extensions-for-google-data-cloud?e=48754805&hl=en) These extensions allow for the automatic installation of custom commands, MCP servers, and more through a simple command. I thought this extension could be useful for my MCP server tool, [ToolsForMCPServer](https://github.com/tanaikech/ToolsForMCPServer). This repository allows ToolsForMCPServer to be installed via the Gemini CLI extensions.

# How to install ToolsForMCPServer-extension

## 1. Install Gemini CLI and default settings

**1. Install Gemini CLI**

```bash
npm install -g @google/gemini-cli
```

**2. Authorization**

You can see how to authorize at [https://github.com/google-gemini/gemini-cli?tab=readme-ov-file#-authentication-options](https://github.com/google-gemini/gemini-cli?tab=readme-ov-file#-authentication-options).

## 2. Copy a Google Apps Script project

After you log in to your Google account, access the following URL using your browser. And, copy the project by clicking the copy button at the top right.

[https://script.google.com/home/projects/1Qm9LgtuQLxDzdLUoJPrOEpmyTBivZZsCLiSUC7q-D3Gi4fISvxgcITWb](https://script.google.com/home/projects/1Qm9LgtuQLxDzdLUoJPrOEpmyTBivZZsCLiSUC7q-D3Gi4fISvxgcITWb)

By this, the copied Google Apps Script project is automatically opened.

## 3. Deploy Web Apps

To allow the Gemini CLI to communicate with our script, we must deploy it as a Web App. This creates a unique URL that acts as our MCP server endpoint.

You can find detailed information in [the official documentation](https://developers.google.com/apps-script/guides/web#deploy_a_script_as_a_web_app).

Please follow these steps to deploy the Web App in the script editor:

1.  In the script editor, at the top right, click **Deploy** -> **New deployment**.
2.  Click **Select type** -> **Web App**.
3.  Enter a description for the Web App in the fields under **Deployment configuration**.
4.  Select **"Me"** for **"Execute as"**. This is crucial, as it allows the script to run with your permissions to access your Google services.
5.  Select **"Anyone"** for **"Who has access"**. This makes the URL callable from the internet. Access is controlled by the unguessable URL and the `accessKey` defined in the script.
6.  Click **Deploy**.
7.  After authorizing the necessary scopes, copy the **Web app URL**. It will look similar to `https://script.google.com/macros/s/###/exec`. This is your MCP server endpoint.

**Important:** When you modify the Apps Script code, you must create a new deployment version to publish the changes. Click **Deploy** > **Manage deployments**, select your active deployment, click the pencil icon, and choose **"New version"** from the Version dropdown. [More info here](https://github.com/tanaikech/taking-advantage-of-Web-Apps-with-google-apps-script?tab=readme-ov-file#redeploy).

## 4. Environmental variables

This MCP server uses the following 2 environmental variables. Please set them.

API key for using Gemini API. (This variable might have already been set for using Gemini CLI and Gemini API, depending on the environment.)

```bash
export GEMINI_API_KEY="{Your API key}"
```

Web Apps URL retrieved from the above section.

```bash
export MCP_WEB_APPS_URL="https://script.google.com/macros/s/###/exec?accessKey=sample"
```

**Here, `sample` of `accessKey=sample` is from `new MCPApp.mcpApp({ accessKey: "sample" })` in the Google Apps Script "ToolsForMCPServer_project". When you want to modify the access key, please modify both. And, deploy the Web Apps again to reflect the latest script.**

For example, these variables can be set to a file `.bashrc` or `.bash_profile` for bash.

## 5. Install Gemini extension

Run the following command on the terminal.

```bash
gemini extensions install https://github.com/tanaikech/ToolsForMCPServer-extension
```

## 6. Testing

Run the following command on the terminal.

```bash
gemini
```

When the Gemini CLI is opened, run the following command.

```
/mcp
```

When you can see the tools from the MCP server, the setup was finished.

# Sample prompts

The sample prompts using the tools of this MCP server are as follows.

- [Gemini CLI with MCP Server: Expanding Possibilities with Google Apps Script](https://medium.com/google-cloud/gemini-cli-with-mcp-server-expanding-possibilities-with-google-apps-script-4626c661ac81)
- [Gemini CLI: Featuring an Enhanced ToolsForMCPServer](https://medium.com/google-cloud/gemini-cli-featuring-an-enhanced-toolsformcpserver-7afaadfb5cfa)
- [Next-Level Data Automation: Gemini CLI, Google Sheets, and MCP](https://medium.com/google-cloud/next-level-data-automation-gemini-cli-google-sheets-and-mcp-e6628a382e90)
- [Managing Google Docs, Sheets, and Slides by Natural Language with Gemini CLI and MCP](https://medium.com/google-cloud/managing-google-docs-sheets-and-slides-by-natural-language-with-gemini-cli-and-mcp-62f4dfbef2d5)
- [Next-Level Data Automation: Gemini CLI, Google Calendar, and MCP](https://medium.com/google-cloud/next-level-data-automation-gemini-cli-google-calendar-and-mcp-1b9e39e75f34)
- [Enhanced Guide to Using Prompts in Gemini CLI](https://medium.com/google-cloud/enhanced-guide-to-using-prompts-in-the-gemini-cli-817cbce97e46)
- [Next-Level Classroom Automation: Gemini CLI, Google Classroom, and MCP](https://medium.com/google-cloud/next-level-classroom-automation-gemini-cli-google-classroom-and-mcp-ac4bb9103fa6)
- [Unifying Google Workspace with Natural Language: Integrated Collaboration through Gemini CLI and MCP](https://medium.com/google-cloud/unifying-google-workspace-with-natural-language-integrated-collaboration-through-gemini-cli-and-a40489ddf17e)
- [Streamlining Web Page Insights with Natural Language using Gemini CLI, Google Analytics, and MCP](https://medium.com/google-cloud/streamlining-web-page-insights-with-natural-language-using-gemini-cli-google-analytics-and-mcp-1774d2b735b7)
- [Google Maps with Natural Language: Integrated Collaboration through Gemini CLI and MCP](https://medium.com/google-cloud/google-maps-with-natural-language-integrated-collaboration-through-gemini-cli-and-mcp-07ba309593b3)
- [Streamlining Content Creation: A Guide to Using Gemini CLI, MCP Server, and VSCode](https://medium.com/google-cloud/streamlining-content-creation-a-guide-to-using-gemini-cli-mcp-server-and-vscode-e623c42419f5)

---

<a name="licence"></a>

# Licence

[MIT](LICENCE)

<a name="author"></a>

# Author

[Tanaike](https://tanaikech.github.io/about/)

[Donate](https://tanaikech.github.io/donate/)

<a name="updatehistory"></a>

# Update History

- v1.0.0 (October 15, 2025)

  1. Initial release.

- v1.1.0 (October 31, 2025)

  1. `timeout` was added to `gemini-extension.json`.

[TOP](#top)
