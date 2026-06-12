---
title: "Using Ubuntu to delete a file in the Windows partition"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by fishpasteuk on 2011-04-17
Hello,
   I am completely new to Ubuntu and have a rather specific problem that I have been unable to find a solution to on this forum so far, so am posting in the hope that someone will be able to assist me out of a very desperate situation.

I have a machine that is running Windows 7-64bit and being security concious recently started using a Yubikey ([http://www.yubico.com/yubikey](http://www.yubico.com/yubikey)) to protect passwords using LastPass. 

This morning I went one further and decided to use a program  called Rohos Logon Key that allows you to use a Yubikey to strengthen your Windows login. Because I wasn't careful enough and didn't properly configure and test the Yubikey (*facepalms self repeatedly*) I have effectively been locked out of my machine for good.

My only hope is the advice on the Rohos website here: [http://www.rohos.com/support/knowledge-base/what-if-i-cannot-log-on-using-the-usb-key/#pc_nb](http://www.rohos.com/support/knowledge-base/what-if-i-cannot-log-on-using-the-usb-key/#pc_nb)

> 
[B][I]It is necessary to start the computer under another operating system. You could boot it with a Linux Live CD (such as Knoppix Linux or Ubuntu Linux) or a Windows Live CD. Such a CD-ROM can be purchased in any shop which sells computer CD/DVD disks with programs.
Then you need to delete the file c:\program files\rohos\welcome.exe (if you are using a Linux Live CD you will need to move into the windows partition using the program ‘mc’).[/I][/B]
Restart the computer in safe mode (press F8 during startup) and log on using your password.
Delete the program Rohos Logon Key and resart the computer in normal mode. Logon with your password

Being a complete ignoramus when it comes to Ubuntu I wonder if anyone would be able to walk me through the process needed to do this i.e. delete a program from the Windows partition. I will be installing the 10.10 Desktop Edition shortly and will send eternal prayers of thanks to anyone who can hold my hand through all this.

Many thanks,

James

---

### Post by Paddy Landau on 2011-04-17
James, you don't have to install Ubuntu to do this (although, if you wish to install it, we'd be happy to help).


[LIST=1]
[*]Create a Live CD. This can be on a CD or a USB stick. Instructions on the [download page]("http://www.ubuntu.com/desktop/get-ubuntu/download").
[*]Boot from the Live CD. Choose to "Try Ubuntu", not to install it.
[*]Once Ubuntu has booted (it takes quite a long time running from USB and even longer running from CD), you will see some menus on the top row of your screen.
[*]Select "Places". You should see your Windows drive listed there. Simply select that drive, and you will be able to find the file you want. Just in case, I would suggest that instead of deleting the file, you rename it; say, *welcome.exe.bak*.
[*]Shut down the computer, remove your Live CD, and continue with the instructions from Rohos.
[/LIST]

Good luck.

---

### Post by HermanAB on 2011-04-17
Howdy,

Boot any Linux CDROM (Ubuntu, Fedora, Suse, Knoppix...), click the Windows drive and delete the file.

Describing it in any more detail would be a waste of time.

---

### Post by Morbius1 on 2011-04-17
Considering the self described lack of experience with Ubuntu or Linux in general I thought Paddy Landau's post was exactly what the user requested.

---

### Post by Leppie on 2011-04-17
> **Morbius1 said:**
> Considering the self described lack of experience with Ubuntu or Linux in general I thought Paddy Landau's post was exactly what the user requested.
that sounds more like lack of computer experience.

---

### Post by fishpasteuk on 2011-04-17
Paddy - just burning the disc now and will let you know how I get on. Thank you so much for the prompt reply.

---

### Post by Paddy Landau on 2011-04-17
> **fishpasteuk said:**
> Paddy - just burning the disc now and will let you know how I get on. Thank you so much for the prompt reply.
NP. I'll check back in an hour or so in case you have questions or difficulties.

---

### Post by fishpasteuk on 2011-04-17
Paddy - Created the Live CD, and attempted a boot, but the Starting Windos icon and Windows login page load as normal and the CD, after a couple of attempts at something simply stops. There is quite a bit of hard drive activity for about 10 minutes, or so, but that just peters out and I'm left twidding my thumbs and cursing.

Can I just double check that I'm not doing anything wrong. I did the following:

1. Went to [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) and followed all the instructions, downloading the 64bit version.

2. Burnt the iso files using a right click and 'Burn to disc image' making sure to verify it too.

3. Turned off the machine and opened the CD drive, inserting the CD and rebooted.

4. Other than a flash of black during startup that seemed additional to usual, and as mentioned above a couple of loading noises by the CD drive and some heavy hard drive activity for ten minutes or so. After up to 45 minutes (I've tried multiple times) nothing happened.

5. I also tried the CD on an identical spec machine that doesn't have the Rohos installed and had exactly the same issue.

Is there anything I might be missing or might a pen drive be more likely to result in a clean boot?

Many thanks,

James.

---

### Post by oldfred on 2011-04-17
Ubuntu has become a higher end system and often the newer versions have video issues. From liveCD when first starting:

boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.

For something quick like you are doing any of the lighter weight Linux CDs might be better. They tend to use default lower end graphics, but you do not need much. Most distributions include the NTFS driver so you can browse and delete files in windows.

Because Linux does not hide any windows files (like windows does), you do have to be careful not to delete anything else.

[http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552](http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552)
Slitaz, DSL, Puppy, Crunchbang, Slackware, Zenwalk, Vector
Also Knoppix

---

### Post by fishpasteuk on 2011-04-17
Old Fred - Thanks for your help. I am a bit confused, however by your instructions below:

> **oldfred said:**
> From liveCD when first starting:

boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.


When you say 'press any key at accessibility circle and keyboard' do you mean click on the Ease of Access icon and then highlight any of the 6 check boxes? It's the 'and keyboard' bit that confusing me. Also, am I to hold down anything together? I'm afraid that I can see, or nothing is loading, that could be a 'nomodeset option' either.

Could you clarify for me, please and bear in mind that I am not familiar with a lot of what you might tell me so you will have to spell it out step by step, as though you're trying to explain it to your elder mother-in-law.

Many thanks,

James.

---

### Post by oldfred on 2011-04-17
The version I have used has a stick figure and keyboard that shows only for a few seconds. When you hit any key then you get what used to be the old style choices of f keys. Under f6 should be an option for nomodeset.

About a page down this shows screen:
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Paddy Landau on 2011-04-18
> **fishpasteuk said:**
> 4. Other than a flash of black during startup that seemed additional to usual, and as mentioned above a couple of loading noises by the CD drive and some heavy hard drive activity for ten minutes or so. After up to 45 minutes (I've tried multiple times) nothing happened.
Hmm, 45 minutes is way over the top. It should take about 5 minutes or less from a CD, and 3 minutes or less from a USB (on a modern computer).

When you say, "additional to usual," is the computer booting into Windows, or do you end up with a black screen?

I should have added to my instructions that it can be very helpful to have the computer connected to the Internet via Ethernet when you boot. The Live CD will automatically download any additional drivers if required.

---

### Post by Zimmer on 2011-04-18
It might just be that everyone has forgotten to tell the OP how to make his BIOS boot from the CD drive?

Enter the BIOS setup and change the boot order so that the cd drive is first... ??

---

### Post by fishpasteuk on 2011-04-18
I just wanted to say a huge thank you to everyone who helped me on this forum. Although the solution that had been suggested to me didn't work out, it was heartening to receive your effort and time. It was very much appreciated.

In the end I miraculously managed to break into Safe Mode (despite Rohos Logon Key specifically assuring those who buy it that this cannot happen) and then could happily delete away. Machine now Rohos free, thank God, and staying resolutely that way.

Many thanks, once again, for those who took their time to try to solve my problem.

James.

---

### Post by Paddy Landau on 2011-04-19
That must be a great relief for you, James.

If you are worried about security, I wouldn't over-protect logins, because (as you have learned) you can get to your files anyway by other means. Look at something like [TrueCrypt]("http://www.truecrypt.org/"), which will protect your data to a very high degree. Just be sure to make adequate backups, because if you forget your passphrase, you simply cannot recover your data.

Please mark this thread as Solved.

---

### Post by fishpasteuk on 2011-04-19
> **Paddy Landau said:**
> That must be a great relief for you, James.

If you are worried about security, I wouldn't over-protect logins, because (as you have learned) you can get to your files anyway by other means. Look at something like [TrueCrypt]("http://www.truecrypt.org/"), which will protect your data to a very high degree. Just be sure to make adequate backups, because if you forget your passphrase, you simply cannot recover your data.

Please mark this thread as Solved.

Paddy - the relief after managing to do this was visible from space. Thanks for the tip about TrueCrypt, I'm looking into it now, and will be proceeding with caution and full back ups.
Many thanks,
James.

---

