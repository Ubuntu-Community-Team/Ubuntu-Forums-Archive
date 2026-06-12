---
title: "Lubuntu does not recognize wifi"
date: 2014-06-04
forum: Networking &amp; Wireless
---

### Post by spi_ on 2014-06-04
hello, apology from my English, I have installed in USB the new lubuntu version, I have wifi network, the others two USB linux (Ubuntu, Fedora) recognize automaticaly  my wifi network, but lubuntu not recognize, why happens this? what can I do? I wait for your answer, thanks a lot...

---

### Post by sudodus on 2014-06-04
Lubuntu is not running ***nm-applet*** (Network Manager applet) due to a bug, but it is there and can be activated easily (in most cases). See this text (and links) from the release notes

> 
[LIST]
[*]Network indicator on the panel may not start  at login. You can start it manually by launching "nm-applet" in a  terminal. Some others autostarted applications may also be affected  (such as automatic updates). See [1308348]("https://bugs.launchpad.net/bugs/1308348") for the details and the ETA for the fix. To turn on nm-applet in autostart, follow [these instructions]("http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html") It may need two reboots to fully work. 
[/LIST]


---

