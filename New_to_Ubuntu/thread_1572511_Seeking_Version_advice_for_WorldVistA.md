---
title: "Seeking Version advice for WorldVistA"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by IDispose on 2010-09-11
We are looking into setting up WorldVistA (an EMR and Medical Practice Management software based in Veterans Admin's VistA). The client software can run on windows or Linux desktops. For the database the options are to run Intersystem's Cache on windows which requires a windows license or choose FIS's GT.M.

Question:
To host GT.M on a Linux based OS, should we choose Ubuntu server or Desktop? I am a Linux newbie with good experience in the windows world. Will be more comfortable working with a GUI.

Will choosing desktop Ubuntu to host GT.M cause issues when solution is deployed?

Any help highly appreciated

thanks

---

### Post by jtarin on 2010-09-11
There are ways to get a working GUI on an Ubuntu server, but then you have a different level of security to contend with....not impossible but another hole to cover.[Here's a link]("http://www.linuxquestions.org/questions/ubuntu-63/gui-for-ubuntu-server-463053/") to some conversation on the subject.

---

### Post by hhlp on 2010-09-11
If you wan to install a graphical desktop manager without some of the desktop addons like Evolution and OpenOffice, but continue to use the server flavor kernel use the following command :

```
sudo aptitude install --no-install-recommends ubuntu-desktop
```

---

### Post by IDispose on 2010-09-11
@hhlp, @jtarin
Thanks for the quick response. I'll check out the desktop on server options.

However one more thing I would like to know is, Is running the desktop version basically server + GUI + some security holes unplugged? Is running a business that used GT.M database on desktop recommended? 

For example, I can run MS SQL Server on Windows 7 but running a business I definitely would want to run MS SQL Server on windows server machine. Windows 7 and Windows server are 2 different animals. Is the case similar with Ubuntu Desktop and Server of is the desktop essentially a server with pretty GUI? 

Thanks again!

---

### Post by jtarin on 2010-09-11
I would just start with the server and add what you need so there is no doubt in your mind but you can always install a desktop run your applications in that environment and see if that is suitable for you. It's really a question that can't be answered for an individual. You have to decide what level of comfort, security, confidence and ease of operation is good for you.Ask yourself what you need in a GUI that makes it imperative.Possibly you don't need to install a desktop and there is some front-end GUI that will fit the bill. Sometimes just a file-manager,browser for administering something like Webmin or whatever GUI that might come with your application, but whatever you decide in the terms of GUI it's the X windowing system that will be you biggest security concern, as it would be on MS running a GUI.The difference would be you have more control with Linux than MS.

---

### Post by IDispose on 2010-09-11
@jtarin
Thanks for the further clarifications. I think like you suggested, getting familiar with Ubuntu desktop and then moving to the server edition for real business deployment is the good path. 

Thanks again for your time

---

### Post by jtarin on 2010-09-11
Your more than welcome. I'm happy to have helped.

---

