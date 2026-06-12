---
title: "how can i delete partitions on ubuntu?"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by Sonicrulz12 on 2010-12-20
I'm running Ubuntu 10.10 and i would like to know how to delete partitions through ubuntu

---

### Post by wilee-nilee on 2010-12-20
Can you be be more specific, we see people delete partitions and have no bootable setup. Your asking for help with no specificities.

---

### Post by amjjawad on 2010-12-20
> **Sonicrulz12 said:**
> I'm running Ubuntu 10.10 and i would like to know how to delete partitions through ubuntu

If that partition which you want to delete is not being used by Ubuntu nor any other OS then:
You need to install GParted.

From Terminal:
```
sudo apt-get install gparted
```

---

### Post by Sonicrulz12 on 2010-12-20
the partition is being used by ubuntu, you see i have the desktop and netbook editions on my computer and wanted to delete the netbook edition partition.

---

### Post by amjjawad on 2010-12-20
> **Sonicrulz12 said:**
> the partition is being used by ubuntu, you see i have the desktop and netbook editions on my computer and wanted to delete the netbook edition partition.

In that case, you need to boot your machine from the LiveCD/USB of Ubuntu.

This is not an easy job to do if you don't know what are you doing. No offense, but if you'll do something wrong, your machine will stop booting.

Edit:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

This will help you and us to remove the un-wanted partition. Please post back the result and wrap up the text with "CODE" tags or click "#".

---

### Post by Sonicrulz12 on 2010-12-20
okay just givesometime to make a live disk

---

### Post by amjjawad on 2010-12-20
> **Sonicrulz12 said:**
> okay just givesometime to make a live disk

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

After that, don't forget to check MD5SUM for your downloaded iso file.
Step1 in my signature will tell you all what you want to know about that.

---

### Post by Sonicrulz12 on 2010-12-20
actually i thought about it im not really going to delete the partion i think its going to be easier if i install ubuntu again and back up all my stuff sorry for taking away your time

---

### Post by cgroza on 2010-12-20
If you do it make sure that the GRUB bootloader is not there.

---

### Post by amjjawad on 2010-12-20
> **Sonicrulz12 said:**
> actually i thought about it im not really going to delete the partion i think its going to be easier if i install ubuntu again and back up all my stuff sorry for taking away your time

No need to apologize :)

Ok, backup your important data and start all over again. If you want to install only one OS (ubuntu) and remove/get rid of everything else then make sure to format and start the installation.

Good luck and if you need anything else, let us know ;)

---

### Post by Sonicrulz12 on 2010-12-20
Okay Thank you hopefully nothing goes wrong

---

### Post by amjjawad on 2010-12-20
> **Sonicrulz12 said:**
> Okay Thank you hopefully nothing goes wrong

Nothing will go wrong if you'll follow the correct procedure :)

Some suggestions that will help you:
1- While you're booting from the LiveCD/USB, use GParted (System > Administration > GParted) to format your HDD but make sure you have nothing valuable there. A backup should be made before that.

2- Make sure to use the right scheme to partition your HDD.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

3- If you have a large HDD (say 250GB or more) then I suggest to keep some "unallocated space" for a future usage. Don't allocate the whole HDD to Ubuntu if you're going to use Ubuntu only. Even that unallocated space could be used later on as a data partition or to install another OS for example. However, it's totally up to you, it's just a thought.

4- Some links and useful info in my signature. See whatever is helpful for you. There's a facebook's page with lots of links.

5- If you decide to keep everything as it's and still want to remove that partition, let us know :)


Good luck!
And you're welcome :)

---

### Post by Sonicrulz12 on 2010-12-20
alright thank you for the help

---

### Post by amjjawad on 2010-12-21
> **Sonicrulz12 said:**
> alright thank you for the help

Anytime :)

---

