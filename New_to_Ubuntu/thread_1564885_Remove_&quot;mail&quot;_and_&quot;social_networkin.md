---
title: "Remove &quot;mail&quot; and &quot;social networking thing&quot; icons from panel"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by JKJ on 2010-08-31
Hi folks

I have just installed Ubuntu 10.4 netbook remix on my netbook and is quite satisfied, but i want to remove these two icons from the panel:

[IMG]http://img197.imageshack.us/img197/591/fjern.png[/IMG]
I'm not going to use them anyway. How can i do that?

Extra question: How can i make the sidebar around the buttons totally transparent? 

[IMG]http://img197.imageshack.us/img197/7932/transppe.png[/IMG]
Like that area.   :D

/Jonas

---

### Post by TNT1 on 2010-08-31
> **JKJ said:**
> Hi folks

I have just installed Ubuntu 10.4 netbook remix on my netbook and is quite satisfied, but i want to remove these two icons from the panel:

[IMG]http://img197.imageshack.us/img197/591/fjern.png[/IMG]
I'm not going to use them anyway. How can i do that?



/Jonas

Dunno how, as they are part of indicator applets. I would just use Cairo Dock and ban the panels. Although I have seen something here that was about going and editing the back end of the applets to change it. Dunno.

---

### Post by Calash on 2010-08-31
Right click on the user name and select remove to get rid of the indicator-me menu.

The mail is a bit more difficult as it is tied into the notification area.  You best bet is to uninstall indicator-messages from synaptic.

---

### Post by TNT1 on 2010-08-31
> **Calash said:**
> Right click on the user name and select remove to get rid of the indicator-me menu.
.

Doesn't that remove the session changer as well?

---

### Post by migs73 on 2010-08-31
Yes it does! I just tried it. If you go to synaptic and remove the 'indicator-me' package and the 'indicator-messages' package it will get the desired effect.

After that you will need to remove the applet from the panel and then add them again, Right click on panel, add to panel, select Indicator Applet and Indicator Applet Session to get your newly modified version.

EDIT: If you cannot add to the panel for whatever reason (as below), a reboot should give you the new look applets.

---

### Post by Calash on 2010-08-31
> **migs73 said:**
> Yes it does! I just tried it. If you go to synaptic and remove the 'indicator-me' package and the 'indicator-messages' package it will get the desired effect.

After that you will need to remove the applet from the panel and then add them again, Right click on panel, add to panel, select Indicator Applet and Indicator Applet Session to get your newly modified version.

This.

I thought you wanted to get rid of the while thing, sorry about that.  The instructions above will get you what you need.

---

### Post by JKJ on 2010-08-31
> **migs73 said:**
> Yes it does! I just tried it. If you go to synaptic and remove the 'indicator-me' package and the 'indicator-messages' package it will get the desired effect.

After that you will need to remove the applet from the panel and then add them again, Right click on panel, add to panel, select Indicator Applet and Indicator Applet Session to get your newly modified version.

Worked perfectly. Could not remove and add the applets because the panel is locked, but it worked anyway.

Thanks..=D>

---

### Post by axwack on 2010-09-02
For those looking for a fix to get rid of the social networking, this also worked for me.

---

