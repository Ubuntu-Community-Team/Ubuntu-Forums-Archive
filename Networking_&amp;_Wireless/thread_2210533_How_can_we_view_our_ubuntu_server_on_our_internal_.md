---
title: "How can we view our ubuntu server on our internal network through the browser?"
date: 2014-03-11
forum: Networking &amp; Wireless
---

### Post by cheerPuncH on 2014-03-11
Hi,

How can we view our ubuntu server (Ubuntu 10.04.4 LTS) on our internal network through the browser? For example...

```
ionadmin@GQZ0QS1:/results/plugins$ ls
Alignment         ERCC_Analysis  FilterDuplicates  IonReporterUploader  plugin_functions  sampleID  TorrentSuiteCloud
coverageAnalysis  FileExporter   implementations   IonTorrentPanel1     RunRecognitION    scratch   variantCaller

```

I want to physically type in my browser a name associated with the server [http://testing.aib.com/results/plugins](http://testing.aib.com/results/plugins) and see all the directories in my browser.

Thanks,
J

---

### Post by Kirboosy on 2014-03-11
Simple way you could do that is add to your **/etc/hosts**

```
*<LAN-ip address-to-server*> testing.aib.com *<any-other-names> <go-here-that-you-want> <separate-them-by-a-space>*
```

Or the more advanced way would be to setup a BIND server on your network and use that with manual entries. 

The hosts entries would need to be entered on each computer needing to connect. Whereas the [BIND]("https://help.ubuntu.com/community/BIND9ServerHowto") setup would cover everyone on the network as it would be your DNS server. However setting up BIND could be annoying and is more permanent on the network.

For the handling of showing files you would either need to configure [apache]("http://httpd.apache.org/docs/2.2/mod/mod_autoindex.html") or [nginx]("http://nginx.org/en/docs/http/ngx_http_autoindex_module.html") (depending on what one you prefer) to handle displaying the directories contents.

Hope that helps!
~Caboose

---

