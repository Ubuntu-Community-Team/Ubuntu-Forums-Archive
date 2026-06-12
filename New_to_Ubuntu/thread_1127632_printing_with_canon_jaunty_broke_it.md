---
title: "printing with canon jaunty broke it"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by tropdoug on 2009-04-16
That's probably not quiet correct however - I used to be able to print with my Canon LBP3200 Laser under all variants. But with Jaunty whenever the command /etc/init.d/ccpd start is given something crashes. I have tried to use the apport debugging tool, but after gathering information it tells me that the problem lies with 'cndrvcups-capt' which is the canon driver, and not a ubuntu program therefore not able to be debugged by the community. fair enough I thought. 

So has anyone else experienced the loss of being able to print under jaunty when they used to be able to under other versions? if so anyone got any ideas of what I could do.

I have installed carefully both the 1.6 and the 1.8 variants of the canon driver from their websitre both do exactly the same. I can still print from a virtual box using XP (would rather not though) 

any ideas?

---

### Post by cariboo on 2009-04-16
Have you contacted Canon about the problem?

Jim

---

### Post by tropdoug on 2009-04-17
Thanks Jim

I have searched the Europe site but so far haven't found a way to directly email them. However if the driver worked on the last 4 Ubuntu versions, but not on the latest wouldn't you agree that the issue probably lies with this version of OS, as that is what has changed and not the driver (I have re installed the driver on a computer with 8.10 on it, and it works well, but I want to use Jaunty)

One thing that was different with the jaunty install is that the driver installation calls for issuing the command as follows 

```
douglas@desktop:~$ /etc/init.d/cupsys restart
bash: /etc/init.d/cupsys: No such file or directory
 **If I do:- **

douglas@desktop:~$ sudo /etc/init.d/cupsys restart
sudo: /etc/init.d/cupsys: command not found

[B]so then I tried:- 

[/B] douglas@desktop:~$ sudo /etc/init.d/cups restart
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
  
```As can be seen cupsys wont work, and I have found that it is no longer included in the files anywhere. 

However if I just do sudo /etc/init.d/cups restart it seems to be OK, but maybe it's not and that is where the issue lies. Remember I am just guessing here.

---

### Post by tropdoug on 2009-04-20
Bump

---

### Post by aeiah on 2009-04-20
well it seems like the driver might try to call cupsys instead of cups? maybe there are other naming differences that are causing problems.

is the driver installation script a readable shellscript that you can change pathnames for? you could try that, or you could try creating the right symlinks from cups to cupsys etc.

you might find more success just waiting until there's a bugfix or patch. i suspect there's gonna be a lot of people with similar problems as there always is when ubuntu decides to rename a daemon.

---

### Post by Denis Clijsters on 2009-04-20
Same problem here. However, it worked in Jaunty 3 weeks ago but suddendly, after an update during that time (I'm not sure when exactly since I don't use my printer every day) it stopped working.

Id do have Jaunty 64 bit, Canon LBP 5100....

---

### Post by cjgainer on 2009-04-25
Hi all. 

Sorry i have no further help, but I am reporting the same problem...

Jaunty amd64
AMD 6000+
Canon mp530

As soon as i try to print, i get all kinds of crazy graphics breaking up, and the system becomes unusable. Once this happens, I cant even ctrl+alt+f1,2,3... to try to kill the process.

I have been using Hardy ---> Intrepid with no related problems at all until now. I have always used the Canon mp500 driver, which has been fine.

---

### Post by dgavenda on 2009-04-25
Ditto what cjgainer said.  Seems like we have similar setups and same problem.  

Jaunty amd64
AMD 6000+
Canon mp530

It worked fine in 8.04/8.10.  With jaunty it fails every time.  Submitted a bug last wk: [https://bugs.launchpad.net/ubuntu/+bug/364877](https://bugs.launchpad.net/ubuntu/+bug/364877)


Oh, it works fine on a laptop that still have 8.10 on it.  So much for having this AMD64 box be my "print server" at least for the moment.

---

### Post by tropdoug on 2009-04-26
Hmm seems that when the developers wrote something new in jaunty it has broken the ability of this version to print to canon lasers. So my question now is, after finally getting a driver officially available from Canon that worked, how can we get the Jaunty developers to look at the issue and see what they changed that made Canons driver unusable?

Does anyone know how to do this?

---

### Post by stephenr80 on 2009-04-27
same problem here with Canon 2900, spent whole weekend trying to make it work but no chance. I'd put my hand on fire and say that the main problem is what some of you already mentioned: cupsys dissapeared (which caused problems to many people already) and was replaced by cups. All LBP Tutorials speak from cupsys when it comes to start CUPS but it definitely doesnt exist anymore under Jaunty. Hope that someone can make it work!

---

### Post by stephenr80 on 2009-04-29
My printer seems to work perfect but I have a little Prob: when I start Ubuntu and then Turn on the printer, the system detects a second Printer LSB29002 which wont print. I then have to delete this printer and run the command to asign the original printer to the usb port. Any ideas? This is not like in Windows where the printer "sleeps" and then when turned on it will be recognized.

Ah yes! forgot to say I am using it with Jaunty full updated using 1.80 Canon drivers and their installation guide, but using cups instead of cupsys. Everything else keeps being the same.

---

### Post by tropdoug on 2009-05-09
Still trying no luck, except the printer works perfectly under Sun Virtual box win XP -- now I do NOT want to be using windows at all, so my aim is to solve this, abyone else got any ideas we copuld try. 

by the way stephenr80 this happened to me with a 'ghost' LBP3200 (2) appearing in my printer set up, but deleting it and resetting the main one did no good. It just stayed DED!

BUMP

---

### Post by spodesabode on 2009-07-13
Just wanted to add that I'm seeing the same behaviour with my LBP5000. Upgraded from Hardy to Intrepid and then to Jaunty. With Jaunty it broke it. Installed the latest 1.8 drivers and that made no difference. 

I also get the second printer when I plug the device in.

As this is/was my print server for the house, I'm a little upset :(

---

### Post by oldfred on 2009-07-13
I also had a recent event with my Canon MP-160. I think it was after an update to CUPS. I could not get it to print PDF files and it was giving me errors. I had installed for testing Jaunty 64bit version and it printed fine where my Jaunty 32 bit version is an update upon update for the last 2-3 years with some old cruft often causing problems. 
My fix was reinstalling the printer and when it asked to update the config(?) file at the end of the update, I forced it to overwrite my old one with the new default from the maintainer. It has worked ever since.

---

### Post by tropdoug on 2009-07-21
Anyone know how to bring what appears to be a pretty generic bug with jaunty and the missing cupsys file that affects canon printers to the developers notice, and maybe someone can list it as an official bug? I don't know how to do this.

---

