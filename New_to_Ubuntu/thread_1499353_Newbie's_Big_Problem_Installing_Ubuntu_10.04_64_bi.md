---
title: "Newbie's Big Problem Installing Ubuntu 10.04 64 bit"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by adamsiddhi on 2010-06-01
So I tried installing Ubuntu 10.04 64 bit on my computer and severely screwed it up. Rather then explaining the whole problem here I posted it at Super User here:

[[COLOR="Indigo"]**http://superuser.com/questions/147854/problem-installing-ubuntu-10-04-64-bit-side-by-side-with-vista-by-using-a-bootabl**[/COLOR]]("http://superuser.com/questions/147854/problem-installing-ubuntu-10-04-64-bit-side-by-side-with-vista-by-using-a-bootabl")

I am a total newbie to Ubuntu and the Linux-verse so help is drastically needed! 

Thanks,
Adam

---

### Post by Ozymandias_117 on 2010-06-01
Sounds like the first time you exited while it was still partitioning and broke your windows partition.

---

### Post by adamsiddhi on 2010-06-01
> **Ozymandias_117 said:**
> Sounds like the first time you exited while it was still partitioning and broke your windows partition.

I suppose that makes sense. Well all I know is that Vista got banged up. Luckily it was able to be repaired. I just popped into IRC #ubuntu and 2 folks there told me to use 'gparted' to delete the bad Ubuntu partitions & then to reinstall Ubuntu 10.04 with out importing my account settings from Vista. So that is what I will do now. 

*!Fingers crossed!*

---

### Post by blackcobra on 2010-06-01
If gpart doesn't work, all is not lost, the computer just need an operating system!

Reinstall the Vista OS, half of your drive would be in a different format from the other, to access that would  mean downloading Linux reader and installing it in windows. Which would be mess! Put the Vista OS into  computer and boot it from the beginning (ie. from when you turn the computer) Let Vista take up the entire drive (NTFS)! Be sure to have another computer with Internet access beside you. As i don't know the difficulty in reinstalling windows. Its could be easy like Ubuntu or hard!

Or, change to Ubuntu completely. If you go down that road be sure to check if your wireless card is compatible with Ubuntu, as a lot of wireless card are not supported by Ubuntu, a lot are though! Check! most driver are supported.

---

### Post by waynefoutz on 2010-06-01
I'm guessing your Windows file system had errors on it before you even started the first Ubuntu install. If if has errors, it's not uncommon for partitioning to fail. Before you install Ubuntu to dual boot with Windows, it's a pretty good idea to run a scan disk on your drive with Windows to make sure it doesn't have any errors, then it's a good idea to defrag it. Normally if the Ubuntu installer sees file system errors it will abort the partitioning operation before it starts, but as you found out, that's not always the case. 

Another tip: after Ubuntu is successfully installed, the next time you boot up Windows it will want to run a scandisk, LET IT FINISH. I cooked a Windows install by hitting the escape key and skipping that scandisk.

---

### Post by adamsiddhi on 2010-06-02
> **waynefoutz said:**
> I'm guessing your Windows file system had errors on it before you even started the first Ubuntu install. If if has errors, it's not uncommon for partitioning to fail. 

Interesting. This seems to be a likely situation as I have not Defragged or Scanned Disk for errors in a long time. 

> **waynefoutz said:**
> Before you install Ubuntu to dual boot with Windows, it's a pretty good idea to run a scan disk on your drive with Windows to make sure it doesn't have any errors, then it's a good idea to defrag it.

I have been thinking about doing this for a while but whenever I defrag it seems like hours go by and I get no work done. I suppose that is why it is good to defrag often. I have set the Vista defragger scheduler to defrag my HD every week but guess what? It does not work. Others have complained about this.  

> **waynefoutz said:**
> Normally if the Ubuntu installer sees file system errors it will abort the partitioning operation before it starts, but as you found out, that's not always the case.

I see. Yes this is a pretty nasty problem when a program/installer just hangs and gives the user no feedback. Showing the end user what is going on in an installation should be a priority. Perhaps my case is ultra rare.

> **waynefoutz said:**
> Another tip: after Ubuntu is successfully installed, the next time you boot up Windows it will want to run a scandisk, LET IT FINISH. I cooked a Windows install by hitting the escape key and skipping that scandisk.

Thanks for this tip and all the ones before. I appreciate it immensely.

---

### Post by adamsiddhi on 2010-06-02
> **blackcobra said:**
> If gpart doesn't work, all is not lost, the computer just need an operating system!

Reinstall the Vista OS, half of your drive would be in a different format from the other, to access that would  mean downloading Linux reader and installing it in windows. Which would be mess! Put the Vista OS into  computer and boot it from the beginning (ie. from when you turn the computer) Let Vista take up the entire drive (NTFS)! Be sure to have another computer with Internet access beside you. As i don't know the difficulty in reinstalling windows. Its could be easy like Ubuntu or hard!

Or, change to Ubuntu completely. If you go down that road be sure to check if your wireless card is compatible with Ubuntu, as a lot of wireless card are not supported by Ubuntu, a lot are though! Check! most driver are supported.

Well I can not reinstall Vista Home Premium OS because I never got the original disk when I bought the computer. That pisses me off. I would be more likely to switch all the way to Ubuntu if it came to that. 

When I loaded Ubuntu from the USB drive I was able to see Wireless networks detected. So I assume that means that my Wireless card was detected. The problem was that I could not connect to my usual Wireless network connection. It gives me an option to enter a password for my WPA2 connection but all I have is the KEY (hex). So if that KEY is not the password then where would I find the password? Because I do not have one.

Thanks.

---

### Post by blackcobra on 2010-06-02
> **adamsiddhi said:**
> Well I can not reinstall Vista Home Premium OS because I never got the original disk when I bought the computer. That pisses me off. I would be more likely to switch all the way to Ubuntu if it came to that. 

When I loaded Ubuntu from the USB drive I was able to see Wireless networks detected. So I assume that means that my Wireless card was detected. The problem was that I could not connect to my usual Wireless network connection. It gives me an option to enter a password for my WPA2 connection but all I have is the KEY (hex). So if that KEY is not the password then where would I find the password? Because I do not have one.

Thanks.

Click on the on the wireless icon >VPN Connections>Configure VPN
>Wireless
Click your connection and
>Edit
>Wireless Security
>None

All the normal type are there.

---

