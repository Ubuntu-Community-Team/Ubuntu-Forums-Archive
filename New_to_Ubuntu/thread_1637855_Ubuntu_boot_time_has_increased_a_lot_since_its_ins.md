---
title: "Ubuntu boot time has increased a lot since its installation"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by pranavk_uict on 2010-12-05
I started using ubuntu 10.10 a few days ago. My laptop now boots ubuntu fine but takes time. If I boot without the splash screen, I can see that it stops after a line which looks like
"Begin: Running /scripts/init-bottom ...done"
then it does nothing after this for a few seconds and then it starts normally. Here is my boot log (output of > cat /var/log/boot.log```

Begin: Loading essential drivers ... done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... done.
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/sda3: clean, 236356/647680 files, 1375514/2589952 blocks (check in 5 mounts)
/dev/sda6: clean, 22658/244320 files, 595611/976384 blocks
init: ureadahead-other main process (1065) terminated with status 4
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                               [ OK ]
 * Setting sensors limits 
```I have also attached my bootchart image. I am totally new to this, and I couldn't figure out the delay in the boot. I need help to reduce my ubuntu boot time. (This is one of the reasons I am trying to switch from Windows to Ubuntu).

---

### Post by Megaptera on 2010-12-05
How long is it taking to boot?
What's the system spec?

---

### Post by pranavk_uict on 2010-12-05
> **Megaptera said:**
> How long is it taking to boot?
What's the system spec?

It is taking around 2 minutes (this varies though- the bootchart that I uploaded says it took 1:35 mins)
My system is
Dell Vostro 1400,
Intel Core2Duo 1.6GHz,
2GB RAM
160GB Hard drive
I have a dual boot (Ubuntu 10.10+Windows7)

---

### Post by Megaptera on 2010-12-06
My Dell, similar specs but Ubuntu only boots in 45 to 60 seconds depending what one regards as fully booted.
I don't see you boot time as a problem 'cos unless you are constantly shutting down & re-booting dozens of times a day those are good timings.
If you are constantly shutting down & re-booting dozens of times a day maybe re-think doing so?

---

### Post by pranavk_uict on 2010-12-06
No, I dont reboot the machine multiple times a day...... But I really wanted to figure something about why the boot stucks at that particular point and takes time. If somehow I manage to do that right, then the boot time will still increase. The thing is I am trying to change some of my friends minds to switch to ubuntu. So, I want to make everything work which we need in our school (which I have done more or less) but still if the boot could become faster.....

---

### Post by oldfred on 2010-12-06
Is it running the fsck on every boot. It should only do that every 30 boots unless you are having some sort of hard drive issue.

I do not know how to understand the drive's smart data, but you can see it under System, Administration, Disk Utility and click on drive in left panel and then on smart data in the right panel.

If you want to see the fsck separately to see if it is finding errors.

Change to your drive & partitions sda3 and sda6

From liveCD so everything is unmounted, change sdb1 to your partition(s)
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Kixtosh on 2010-12-06
> **pranavk_uict said:**
> It is taking around 2 minutes (this varies though- the bootchart that I uploaded says it took 1:35 mins)
My system is
Dell Vostro 1400,
Intel Core2Duo 1.6GHz,
2GB RAM
160GB Hard drive
I have a dual boot (Ubuntu 10.10+Windows7)That does seem far too long to me. I installed Ubuntu 9.10 on an ancient Dell with a 400 MHz PII earlier this year, and even that booted up in about 1m 45s or less (I then installed Lubuntu instead, and boot time dropped to about 50-55 seconds).

I have Ubuntu 10.04 now on a Pentium single core 1.2GHz starting in about 50-55 seconds (compared to almost two minutes for a completely fresh install of WinXP with no frills or applications added). On a Core2Duo 1.2GHz the same Ubuntu 10.04 starts in 25 seconds, from pushing the power button to the desktop, with all loading up hard drive activity finished completely (this takes two whole minutes under Vista, and even then the hard drive activity light is still flickering away doing something mysterious).

The 25 second laptop has an OEM Solid State Drive, but that's still only rated 6.3 on the Windows Experience Index, and the overall WEI rating for that laptop is just 2.0 (mostly because of integrated GMA graphics, but all the other scores are fours, fives and sixes). With your specifications, I would certainly expect the total boot time to be 45 seconds or less.

---

### Post by pranavk_uict on 2010-12-07
> **oldfred said:**
> Is it running the fsck on every boot. It should only do that every 30 boots unless you are having some sort of hard drive issue.

I do not know how to understand the drive's smart data, but you can see it under System, Administration, Disk Utility and click on drive in left panel and then on smart data in the right panel.

If you want to see the fsck separately to see if it is finding errors.

Change to your drive & partitions sda3 and sda6

From liveCD so everything is unmounted, change sdb1 to your partition(s)
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

I am attaching a image of my disk's smart data. There is one RED thing over there. I have no idea what that is. Also, can you elaborate a little more about what you described doing through a live cd? I am new to this and I totally lost you after "change sdb1 to your partition".

---

### Post by oldfred on 2010-12-07
It says it is a warning that the drive had to move data around. Some bad sectors is normal, but I would monitor it and make sure I had regular backups. If it starts to grow, then I would look for a new drive.

LiveCD is just the CD you used to install. The other choice from install was try it out on your system and is a fully functional system you can use for repair or just making sure the system works on your hardware.

Partition is the part of the drive where Ubuntu is installed. You can have 4 primary partitions, but one primary can be converted to a extended which is a container that can hold many logical partitions. Windows has to be installed to a primary, Ubuntu can work from either primary or extended partitions.

To see where everything is installed:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

