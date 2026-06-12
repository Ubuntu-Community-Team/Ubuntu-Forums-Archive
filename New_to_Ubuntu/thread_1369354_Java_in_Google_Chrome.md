---
title: "Java in Google Chrome"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by McDarling on 2009-12-31
So I downloaded the self-extracting installation file (not the RPM) [here]("http://java.com/en/download/manual.jsp?locale=en&host=java.com:80"), and followed the instructions given next to the download link, which was fine up until the Enable and Configure step, which gives details for Mozilla, Netscape, and Firefox. I looked at what is supposed to be done for those browsers, and it seems that you just go to the plugins directory for your browser, and create symbolic link to the java executable, usually with a specific name. I can't find the plugins directory for Chrome, and I don't know what I would name the link. Is this possible yet, given that Chrome is still in Beta?
I can use Firefox, but I hate it, and would very much prefer to use Chrome when possible

---

### Post by Ferretti on 2009-12-31
I had this same exact problem. I follow this guide: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) It explains everything needed and I now have the latest Java (Update 17) installed and running on Chrome!

---

### Post by McDarling on 2009-12-31
So I followed that guide as well as I could, but changed the ~/.mozilla directory to ~/.google-chrome. With all that work, I've arrived at this picture. Is chrome not recognizing the plugin? Can I make it?

---

### Post by Ferretti on 2010-01-01
I also went into Synaptic Package Manager and enabled "sun-java6-plugin. After installing that, Java worked perfectly in Chrome.

---

### Post by LeifAndersen on 2010-01-01
^^^Good advice, it made my life much easier^^^

---

### Post by Ferretti on 2010-01-01
Also, to confirm that you are indeed on the newest version of Java. You can go here: [http://java.com/en/download/installed.jsp?detect=jre&try=1](http://java.com/en/download/installed.jsp?detect=jre&try=1)

---

### Post by McDarling on 2010-01-01
Thanks alot. Synaptic worked. I'm now fully capable of playing Go online in Chrome!

---

### Post by jamesstansell on 2010-01-02
> **McDarling said:**
> Thanks alot. Synaptic worked. I'm now fully capable of playing Go online in Chrome!

Glad to read that synaptic worked for you.

After a look at [http://java.com/en/download/help/5000010500.xml#enable](http://java.com/en/download/help/5000010500.xml#enable) I would say it's out of date because it doesn't mention the new NPAPI plugin.

[https://jdk6.dev.java.net/plugin2/#INSTALLATION](https://jdk6.dev.java.net/plugin2/#INSTALLATION) has the generic instructions and the link from Ferretti has some great, detailed, ubuntu-specific instructions.  I have to guess that the synaptic package automated those instructions.

Regards,

-james.

---

### Post by jamesstansell on 2010-01-02
> **Ferretti said:**
> I had this same exact problem. I follow this guide: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) It explains everything needed and I now have the latest Java (Update 17) installed and running on Chrome!

Thanks for this link!  I was not aware of that page until now.

Regards,

-james.

---

### Post by Ferretti on 2010-01-02
No problem. Glad I could help!

---

