---
title: "help please"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by lisa_marie on 2009-04-25
when my son tries to down load any thing a window comes up saying launch application- choose an application  i have tried all surly you can down load like u can on windows any help would be great thank u:KS

---

### Post by zvacet on 2009-04-25
Can you be more specific?Where from you tried to download program?Did you used add/remove,synaptic or you try to download from some site?

---

### Post by t0p on 2009-04-25
If you want to download and save a file, you can right-click and select **Save Link As...** option.  Then it will download to your Desktop

---

### Post by Sidewinder1 on 2009-04-25
First of all... Welcome!
It sounds to me like you're trying to download a windows executable program. These will generaly not run in Ubuntu other than through Wine. Things are a little different in Ubuntu. In order to download and install software in Ubuntu, the easiest way is to use Synaptic Package Manager (click on System--->Administration--->Synaptic Package Manager) then highlight, by clicking the software that you wish to install, then click on apply. That's it; the program will be downloaded and installed. The other easy method, in Ubuntu, is to use Add or Remove Programs (click on Applications--->Add/Remove).
HTH,
Side

Again, Welcome and enjoy...

---

### Post by MFinkel on 2009-04-25
Hi Sidewinder1, I hope you can help me with a similiar problem. When I open Adept Manager I get this warning. Read Only mode - Need Root privileges - Adept Manager. The problem is apply changes does not work, so, how do I open Adept Manager and have apply changes work properly? Thanks, Michael.

---

### Post by MFinkel on 2009-04-25
By the way, I am running Ubuntu 8.04.1 LTS Desktop Edition.

---

### Post by MFinkel on 2009-04-25
> **MFinkel said:**
> By the way, I am running Ubuntu 8.04.1 LTS Desktop Edition.
By the way, I am using Ubuntu 8.04.1 LTS Desktop Edition.

---

### Post by llamabr on 2009-04-25
> **MFinkel said:**
> Hi Sidewinder1, I hope you can help me with a similiar problem. When I open Adept Manager I get this warning. Read Only mode - Need Root privileges - Adept Manager. The problem is apply changes does not work, so, how do I open Adept Manager and have apply changes work properly? Thanks, Michael.

Hello, mfinkel.  You should begin your own thread for new questions.

To the OP, what, exactly, are you trying to dload?  Sometimes you have to associate a file with an application to open it.  Usually ubuntu will know, but sometimes it doesn't.

What kind of thing are you dloading?

---

### Post by Sidewinder1 on 2009-04-25
MFinkel, llamabr is correct, you should start a new thread, especially since I have no experience with Adept Manager and I'm running the same version as you 8.04...
Good luck; Title your thread with "Adept Manager" and I'm sure that you'll get plenty of responses. Everyone around here is exceedingly friendly. :-)

---

### Post by calebk on 2009-04-25
Lisa, when the popup comes on the end of the name does it say .exe or .deb

If it says .exe then it is a windows application and you can not download those applications. You can download some .exe programs with a program called wine but that does not always work and sometimes it requires a bit of fiddling.

IF it says.deb on the end then you are installing ubuntu software. Try saving the file to your desktop. On your desktop click on the file and you should be able to install from there. If you cant then right click on the file on the desktop and click properties, click the tab open with and choose Gdebi package installer. 

Hope I helped

---

### Post by wicky_ts on 2009-04-25
I think it is better to name the thread more specificly than help please or please healp. You will get fast and specific replies if you name it properly.

---

### Post by MFinkel on 2009-04-25
> **llamabr said:**
> Hello, mfinkel.  You should begin your own thread for new questions.

To the OP, what, exactly, are you trying to dload?  Sometimes you have to associate a file with an application to open it.  Usually ubuntu will know, but sometimes it doesn't.

What kind of thing are you dloading?

Sorry about not doing a new thread.
I want to update flash players as this is a new install.
I thought the proper way to download was thru the adept manager.
If there is a better way I would be happy to try it!
Any advise is greatly appreciated.

---

### Post by cariboo on 2009-04-25
If you are using Ubuntu, you should be using Add/Remove Programs or Synaptic Package Manager to install packages. It sounds like you are trying to run Adept without root privileges.

If you must use adept, press Alt-F2 and type:

```
gksu adept
```

---

### Post by MFinkel on 2009-04-25
Thanks for the reply.
I tried the gksu adept and also went to Add/Remove Programs. In either place Apply Changes does not work.

---

### Post by MFinkel on 2009-04-25
Actually, I sit corrected. I am able / figured it our how to add programs thru Add/Remove programs. Thanks for the Add/Remove programs tip!!!!!!!!!!!!!!

---

