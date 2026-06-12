---
title: "Debian - start firewall"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by penguin-of-doom on 2009-06-05
Hey,
I do not know how to start my firewall on debian. I worked on OpenSuSE for years and there I knew how to start the firewall... I hope I can get help here ^^ I only want to start my firewall, and I think It would be easy, but I haven't found anything yet.

regards,
penguin-of-doom

---

### Post by bacardiandwatermelon on 2009-06-05
I think firestarter works for debian. Its a nice little gui firewall.

---

### Post by penguin-of-doom on 2009-06-05
thank you! I have installed firestarter sucessfully and now the firewall is active :D
But I have one more question:
is there a good anti-virus program for linux? I do not have any yet, but I think it would be good for me ^^

regards,
penguin-of-doom

---

### Post by porchrat on 2009-06-05
> **penguin-of-doom said:**
> thank you! I have installed firestarter sucessfully and now the firewall is active :D
But I have one more question:
is there a good anti-virus program for linux? I do not have any yet, but I think it would be good for me ^^

regards,
penguin-of-doom

ClamAV is a good anti-virus program. It will remove Windows viruses present on your machine, but even if these viruses are present on a Linux system they won't have an effect. There are currently no viruses for Ubuntu and you can count the viruses throughout history that have targeted Linux systems on one hand so you won't find an anti-virus program for Linux viruses because Linux viruses don't exist.

I think it is also important to mention to you that the firewall is just a way to control iptables. The firewall doesn't block incoming connections, it merely helps you configure iptables. What I'm trying to say is that even before you installed firestarter you were protected as iptables blocks all incoming connections by default.

Another firewall program that is quite nice to use (personally I prefer it over firestarter) is UFW, but it is a command line tool and has no GUI.

---

### Post by bodhi.zazen on 2009-06-05
> **penguin-of-doom said:**
> Hey,
I do not know how to start my firewall on debian. I worked on OpenSuSE for years and there I knew how to start the firewall... I hope I can get help here ^^ I only want to start my firewall, and I think It would be easy, but I haven't found anything yet.

regards,
penguin-of-doom

FYI: The firewall in linux , all modern versions, is iptables. iptables is not a service, it is a kernel module.

The start scripts in RHEL, Fedora, OpenSUSE, these do not start a service, they are bash scripts to configure the firewall.

Ubuntu used ufw, the gui front end is gufw.

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") 

Firestarter is no longer maintained and there can be conflicts with it and ufw.

If you want to know how iptables works, I wrote a primer

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by penguin-of-doom on 2009-06-06
thank you for your answers!
Isn't there a GUI for both? for Firewall and AntiVirus? I think that would be much better for me ^^ And I also want that the programs starts when i start up my computer...

regards,
penguin-of-doom

---

### Post by deanjm1963 on 2009-06-06
> **porchrat said:**
> Another firewall program that is quite nice to use (personally I prefer it over firestarter) is UFW, but it is a command line tool and has no GUI.

There is a GUI for UFW called Gufw available in the repos and on their website [http://gufw.tuxfamily.org/index.html]("http://gufw.tuxfamily.org/index.html")

---

