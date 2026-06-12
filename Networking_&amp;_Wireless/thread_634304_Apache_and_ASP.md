---
title: "Apache and ASP"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by OMRebel on 2007-12-07
Okay, hopefully someone here will know what's going on with this.  I have Apache up and going with all of the mono addons.  I can open up a simple asp.net 2.0 site without any problems.  However, this other site, which is the main one, is giving me an error.  I am getting the following:P

PS - the "apv" is the Alias that I have setup in the config and have Mono working this.

Thanks!


Server Error in '/apv' Application
No child nodes allowed here. (node name: pages) ()

Description: Error processing request.

Error Message: HTTP 500. System.Configuration.ConfigurationException: No child nodes allowed here. (node name: pages) ()

Stack Trace:

System.Configuration.ConfigurationException: No child nodes allowed here. (node name: pages) ()
at System.Web.Configuration.HandlersUtil.ThrowException (System.String msg, System.Xml.XmlNode node) [0x00000]
at System.Web.Configuration.PagesConfigurationHandler.Create (System.Object parent, System.Object configContext, System.Xml.XmlNode section) [0x00000]
at System.Web.Configuration.ConfigurationData.GetConfigInternal (System.String sectionName, System.Web.HttpContext context, Boolean useLoc) [0x00000]
at System.Web.Configuration.ConfigurationData.GetConfigOptLocation (System.String sectionName, System.Web.HttpContext context, Boolean useLoc) [0x00000]
at System.Web.Configuration.ConfigurationData.GetConfig (System.String sectionName, System.Web.HttpContext context) [0x00000]
at System.Web.Configuration.WebDefaultConfig.GetConfig (System.String sectionName, System.Web.HttpContext context) [0x00000]
at System.Web.Configuration.WebConfigurationSettings.GetConfig (System.String sectionName, System.Web.HttpContext context) [0x00000]
at System.Web.HttpContext.GetConfig (System.String name) [0x00000]
at System.Web.Configuration.PagesConfiguration.GetInstance (System.Web.HttpContext context) [0x00000]
at System.Web.UI.TemplateParser.get_PagesConfig () [0x00000]
at System.Web.UI.TemplateControlParser.LoadPagesConfigDefaults () [0x00000]
at System.Web.UI.PageParser.LoadPagesConfigDefaults () [0x00000]
at System.Web.UI.TemplateControlParser..ctor () [0x00000]
at System.Web.UI.PageParser..ctor (System.String virtualPath, System.String inputFile, System.Web.HttpContext context) [0x00000]
at System.Web.UI.PageParser.GetCompiledPageInstance (System.String virtualPath, System.String inputFile, System.Web.HttpContext context) [0x00000]
at System.Web.UI.PageHandlerFactory.GetHandler (System.Web.HttpContext context, System.String requestType, System.String url, System.String path) [0x00000]
at System.Web.HttpApplication.GetHandler (System.Web.HttpContext context) [0x00000]
at System.Web.HttpApplication+<>c__CompilerGenerated1.MoveNext () [0x00000]

---

### Post by OMRebel on 2007-12-07
Bump.

---

### Post by cdmdotnet on 2007-12-29
I'm getting the same, and my site isn't exactly complicated.
I've concluded it's something in the web.config file, 

I plan on removing items from here one by one and seeing where i end up

---

### Post by cdmdotnet on 2007-12-29
I've located the problem to a section of my web.config file

		<pages>

			<namespaces>

				<clear/>

				<add namespace="System"/>

				<add namespace="System.Collections"/>

				<add namespace="System.Collections.Specialized"/>

				<add namespace="System.Configuration"/>

				<add namespace="System.Text"/>

				<add namespace="System.Text.RegularExpressions"/>

				<add namespace="System.Web"/>

				<add namespace="System.Web.Caching"/>

				<add namespace="System.Web.SessionState"/>

				<add namespace="System.Web.Security"/>

				<add namespace="System.Web.Profile"/>

				<add namespace="System.Web.UI"/>

				<add namespace="System.Web.UI.WebControls"/>

				<add namespace="System.Web.UI.WebControls.WebParts"/>

				<add namespace="System.Web.UI.HtmlControls"/>

			</namespaces>

		</pages>

I'm guessing one of these isn't yet supported by mono.

---

