---
title: "Automatic input of WINE command every hour"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by TekMuzik on 2009-10-20
I have a Ubuntu Server (8.04 LTS) on my home network. Since it's on a Dynamic IP I want it to automatically run the command "wine edns.exe -u TekMuzik -p ******" every hour to update my DNS records on ends.org with the correct IP so I can access the server over the internet if the IP changes. Is there anyway I can easily set this up on the server? If it's really hard on the server, and would be easier on a GUI version I could also set it up on my Ubunutu 9.04 Desktop if I had instructions, but I would prefer it on my server. Thanks for any advice.

~Kyle

---

### Post by OpenGuard on 2009-10-20
```
crontab -e
```

Add the following line and save it.
```
* */1 * * * wine edns.exe -u TekMuzik -p ******
```

---

### Post by anagor on 2009-10-20
Also you may try using other dynamic dns services which have native linux applications, check this packages/applications in repositories:

ddclient

ez-ipupdate - works with more dynamic dns services that I thought existed.

ipcheck - works with dyndns.org, probably with others too, I've used it in the past, and among the features it provides it will update dyndns only if the IP had changed, it will also run by itself as a daemon, so you won't need a cron job for it.

ez-ipupdate by the looks of it can be the client you are looking for, definately worth exploring.

---

### Post by TekMuzik on 2009-10-21
Thank you both for your suggestions. I think I'm going to go with the crontab route because I'm just so used to everydns's (the site that use edns.exe) layout, and I've already got everything set up there. But thank you both again.

---

