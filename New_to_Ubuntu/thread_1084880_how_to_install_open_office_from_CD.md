---
title: "how to install open office from CD?"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by Brian_Newbie on 2009-03-02
A friend of mine gave me an open office 3.0.0 CD from a Linux magazine he reads and told me I can install it directly from the CD. He said it's for RPM distros but I can convert it into debian for Ubuntu by using the "alien command."

He did not give me any instructions on how to install and the ordering of the commands including the "alien" one. 

Is there an easy method to install it by using terminal commands after I insert the CD into my computer?

p.s

I use Ubuntu 8.10 intrepid ibex and currently have open office 2.4 installed which I'll likely need to remove.

---

### Post by sanderella on 2009-03-02
You can install Open Office direct from SunSystems at [http://download.openoffice.org/](http://download.openoffice.org/) It's free.

Sorry, I don't know how to do it from the cd.

---

### Post by The Cog on 2009-03-02
I've got a feeling that to convert a .rpm to a .deb is just a case of
**sudo alien thingummajig.rpm**

The debian download from the sun site comes as a tar.gz that unpacks and inside is a whole directory full of .deb files. To install those, you have to change to that directory and run
**sudo dpkg -i *.deb**

---

### Post by llamabr on 2009-03-02
I probably wouldn't bother with that disk you have.  You a more updated version directly from openoffice, then install the deb:

[http://tombuntu.com/index.php/2008/05/08/test-drive-openoffice-3-beta-in-ubuntu/](http://tombuntu.com/index.php/2008/05/08/test-drive-openoffice-3-beta-in-ubuntu/)

Messing with the RPM is possibly more trouble than you need

---

### Post by stchman on 2009-03-02
> **Brian_Newbie said:**
> A friend of mine gave me an open office 3.0.0 CD from a Linux magazine he reads and told me I can install it directly from the CD. He said it's for RPM distros but I can convert it into debian for Ubuntu by using the "alien command."

He did not give me any instructions on how to install and the ordering of the commands including the "alien" one. 

Is there an easy method to install it by using terminal commands after I insert the CD into my computer?

p.s

I use Ubuntu 8.10 intrepid ibex and currently have open office 2.4 installed which I'll likely need to remove.

You can get Openoffice.org 3.0.1 from [www.openoffice.org](www.openoffice.org) website is .deb format.

Softpedia has a tutorial on installing OO3 on Intrepid.

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

If you have Hardy replace intrepid with hardy.

Hope this helps.

---

### Post by Brian_Newbie on 2009-03-02
I've decided to get the most recent version from the open office site rather than mess around with the CD.

Thanks to llamabr & stchman for the step by step instruction links.

Brian

---

