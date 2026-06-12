---
title: "How do I copy files to the file system?"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by john1943 on 2010-06-18
May sound a daft question but I've just migrated from another distro to Ubuntu and still finding my  way around , I'm using Ubuntu 10

I've installed Virtualbox  and want to put my backup file into the proper place.
I accessed the file system and assume that ect/vbox is where the files go, trouble is when I try to copy across I get the message "access denied" how do I overcome this please.

---

### Post by Locke_99GS on 2010-06-18
/etc is owned by root and has 755 permissions. You cannot write to it. Use sudo to temporarily escalate your privilages if you wish to write to that directory.

---

### Post by jtarin on 2010-06-18
> **john1943 said:**
> May sound a daft question but I've just migrated from another distro to Ubuntu and still finding my  way around , I'm using Ubuntu 10

I've installed Virtualbox  and want to put my backup file into the proper place.
I accessed the file system and assume that ect/vbox is where the files go, trouble is when I try to copy across I get the message "access denied" how do I overcome this please.
I use the terminal enter the directory of the file I want to copy and issue the command "sudo cp" <filename> <name of destination>. See "man cp" from the terminal for more information on the cp command.

---

### Post by nothingspecial on 2010-06-18
Put the backup files on external media.

That way, if your computer breaks, you have them.

To answer your question, you have to give your user permission to write to /etc/vbox

But if I were you, I would back up to an external drive.


If you want to know how to change the permissions of /etc/vbox then post back and I will show you, however, I think it is pointless to backup on the same file system.

---

### Post by t0p on 2010-06-18
You are denied access probably because you need to have admin privileges to edit or add files to the /etc directory.  The way to get admin privileges is to use the [sudo]("https://help.ubuntu.com/community/RootSudo") command.  But I don't think that's the solution to your problem.

If you have installed VirtualBox, there will be "hidden" directory in your home directory called .VirtualBox.  This "hidden" directory contains directories called  HardDisks and Machines.  They are the places for backups, methinks.

I think you should go read the documentation for VirtualBox, which you'll find [here]("http://www.virtualbox.org/").

---

### Post by ron999 on 2010-06-18
Hi
Use **sudo nautilus** then copy and paste files anywhere.

---

### Post by t0p on 2010-06-18
OP: nothingspecial is, of course, correct.  Backups should be kept  separately.  For instance, I keep my VirtualBox backups, snapshots etc  on an external HDD, in a directory I imaginatively named VirtualBox.  I  suggest you do something similar.  However, youshould still go look at the VirtualBox documentation, so you will know how to configure VirtualBox to your own requirements.

---

### Post by lisati on 2010-06-18
> **ron999 said:**
> Hi
Use **sudo nautilus** then copy and paste files anywhere.

**sudo** will work most of the time for this example, but **gksudo nautilus** is better. "sudo" is intended for command line stuff, "gksudo" is intended for graphical applications running under Gnome (regular Ubuntu), and "kdesudo" for graphical apps in KDE (e.g. Kubuntu)

edit: <aside>Gazing into my crystal ball: A big "hello" to Locke_99GS.</aside>

---

### Post by john1943 on 2010-06-19
Hi folks,
            Many thanks for your help. I had a backup of VBox and wanted to transfer it into Ubuntu
this solved my problem

> **ron999 said:**
> Hi
Use **sudo nautilus** then copy and paste files anywhere.

---

### Post by john1943 on 2010-06-19
If you have installed VirtualBox, there will be "hidden" directory in your home directory called .VirtualBox.  This "hidden" directory contains directories called  HardDisks and Machines.  They are the places for backups, methinks.

I have a backup of my harddisks and machines but how do I access my "Hidden" directory?

---

### Post by philinux on 2010-06-19
> **john1943 said:**
> If you have installed VirtualBox, there will be "hidden" directory in your home directory called .VirtualBox.  This "hidden" directory contains directories called  HardDisks and Machines.  They are the places for backups, methinks.

I have a backup of my harddisks and machines but how do I access my "Hidden" directory?

Yep thats where they are.

Open your home folder and hit ctrl h or View>Show Hidden

---

