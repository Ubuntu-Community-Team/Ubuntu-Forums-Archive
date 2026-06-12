---
title: "Terminal Services in Ubuntu"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by greavette on 2011-08-26
Hello,

I need some help understanding how the following would work in Ubuntu. 

I know I can install MS Office in Windows Server and use Terminal Services to share MS Office to our Windows XP workstation PC's.

Can something like Terminal Services be installed and used in Ubuntu and if so, what is it called?  I'm not looking to use ltsp to use a thin client to connect our workstations too.  I'd like to keep our workstations running Windows and for select applications (to be determined later), serve some applications from an Ubuntu Terminal Server.  So...what is this called on Ubuntu?

Some thoughts on why I'm looking at this...I'm looking into installing Libre Office on Ubuntu and using a Terminal Services Ubuntu variant to allow our Windows XP workstations to use Libre Office.  Not sure if I have to install anything on the workstation to use Libre Office, but maybe that's a question for the Libre Office forum.

For now, I'm just looking for direction/terminology on what it's called in Ubuntu to share applications on our network just like Terminal Services does.

Just so you know my setup...we use Zentyal for our Domain Controller (running on Ubuntu) and our Windows XP workstations authenticate against Zentyal to connect to our network.  We do use Office 2003 on some or our Windows workstations, but my investigation into what people do with Office shows me that we can safely use Libre Office instead.  I know I could install Libre Office on each PC, but I'd like to test on 1 test workstation how we can install Libre Office on an Ubuntu Server and share that install over our network.  

Thanks in advance for any help/direction you can provide for me.

---

### Post by greavette on 2011-08-29
I've recently discovered ULTEO.  This seems to be just what we are looking to do.  I'll have to investigate ULTEO further to see how it works.

---

