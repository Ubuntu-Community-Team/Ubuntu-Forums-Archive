---
title: "proxy"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by am65 on 2009-09-08
Hello, I recently installed Ubuntu 9.04. Now  I want to update through the Synaptic package handler and I get the following message (translated from spanish, the language of my installation):

"It was not possible to download all the repositories indexes"

Anyway I can browse and surf the internet with Firefox.

Could it be the problem that I need to use a proxy server with authentication?

Thanks

---

### Post by diablo75 on 2009-09-08
It's possible that the software sources needs to be set to use a different server.  Check under System>Administration>Software Sources and next to the "Download From:" click on the box and find your way to the server listings.  You can use the "Choose Best" button to auto-ping about 200 servers and it will select the one with the fastest response time.  After you close all the windows, you'll click the "Reload" button, and you should be able to do your updates through update manager after that and use Synaptic to add/remove packages.

---

### Post by am65 on 2009-09-08
I fixed it. I had to set the proxy parameters in the Synaptic preferences. I thought that it was enough to set the proxy parameters in System > Preferences > Network Proxy.

Thanks anyway

---

