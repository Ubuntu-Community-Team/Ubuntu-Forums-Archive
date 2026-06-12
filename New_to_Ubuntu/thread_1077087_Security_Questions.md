---
title: "Security Questions"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Ravernomina on 2009-02-22
Hey... I'M setting up security on my computer and I was wonder what I should do/get for my computer. I read the security guides buy they added more fog then help. So could u give me some advice please TYVM!!


[SIZE="5"]**_Computer Security setup_**[/SIZE]

  -Tiger is installed
  -rkhunter is installed
  -chkrootkit is installed
  -firestarter is installed
  -denyhosts is installed.
-My file system is mounted as "/"
-nothing is encrypted so far. 

Anything on what I need/what I should do will be thanked and loved and most likely used. TYVM!!!

       Ravernomina

P.S. I came form windows and i was always worried about ym security so please help so my anxiety will go away XD

---

### Post by mcduck on 2009-02-22
Well, I can only say that you don't really need to do anything.

There are no viruses or spyware around so only thing antivirus software can do in Linux is to search for Windows viruses (which, of course, can't actually do anything in Linux..)

The default install doesn't have any running services that would listen for incoming network connections so a firewall doesn't really add any extra. You only need to install one if you install some server software on your machine.

Encryption is only usefull if you need to worry about some evil person getting physical access to your machine and being really interested in your files.

Rootkit hunters of course work, but I must say that the likelihood of actually getting rootkitted is very, very small.

In my experience the default setup is very secure as it is. I've been running Ubuntu since 2005 without any security measures, and without any problems. ;)

---

### Post by Ravernomina on 2009-02-22
its just that im so used to all that stuff and without it I feel "unclean" XD

---

### Post by evilGUI on 2009-02-22
Some other things you might do, change your default SSH port, only allow certain users to login via SSH and use public key authentication. I would also install ufw and only open the ports you need. You can read more about this this [here]("https://help.ubuntu.com/community/AdvancedOpenSSH").

---

### Post by mcduck on 2009-02-22
..of course you only need to change ssh port if you actually have ssh server installed (it's not included by default).

And ufw/Gufw is a tool for configuring the firewall just like Firestarter is. Even if you want to run a firewall you only need one tool, so it's either ufw/Gufw or Firestarter, never both.

---

### Post by Celegorm on 2009-02-22
Probably the most important thing to do to protect a linux system is just to keep it up to date. Malware infects computers by exploiting security holes. If the vulnerability a particular malware program exploits has been patched, then it can't infect your computer.

---

### Post by binbash on 2009-02-22
you don't need anything at desktop pc.And the softwares you installed, do not your box secure.

---

