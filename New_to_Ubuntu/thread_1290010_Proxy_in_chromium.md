---
title: "Proxy in chromium"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by ikon_ on 2009-10-13
Well, I insatalled chromium on my laptop without any fuss, but when I started browsing on it I found out that the local intranet sites are blocked by it.It probably used the proxy server for intranet also . But then I bypassed the proxy server for the intranet sites hoping it would work.But still I am not able to view the intranet sites on chrome while I am able to do it on firefox. So what's the problem?? Can somebody HELP????
:confused:

---

### Post by scorp123 on 2009-10-13
You have to exclude Intranet sites from the proxy ... In Firefox this setting is called "No proxy for .... "  <== and there you add your internal IP range, for example.

In Chromium that would be the "Ignored Hosts" setting:

- Open Chromium
- click on the wrench on the far right (Chromium menu bar)
- click on "Options"
- go to "Under the hood"
- click on "Change proxy settings"
- a new window should have opened
- go to the "Ignored Hosts" tab
- here you have to add hosts and IP ranges from your Intranet

==> tadaaa ... they won't go through the proxy anymore.

---

### Post by ikon_ on 2009-10-13
Well I have done all this before.But it doesn't seem to work.

---

### Post by warddr on 2010-09-23
It's a late response, but if you search google for chromium proxy, this thread shows up really high.

To solve this problem you can run chromium with the command

chromium-browser --proxy-server=*proxyip:port*

If you want to start chromium with proxy from the menu, you can go to 
system --> preferences --> main menu
on the left chose internet, now click the chromium web browser right, and double click it to edit.

Change the command to
chromium-browser %U --proxy-server=*proxyip:port*

---

