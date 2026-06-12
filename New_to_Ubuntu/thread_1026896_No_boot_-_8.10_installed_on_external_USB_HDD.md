---
title: "No boot - 8.10 installed on external USB HDD"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by egrpioneer on 2008-12-31
Please help me boot into Ubuntu. Set bios for FDD first drive, but no action.

hardware: Toshiba Satellite A10 laptop. ASCI Bios 1.3

Thank you!

---

### Post by Coder543 on 2008-12-31
When you installed it did you disable installing the boot loader?

---

### Post by theozzlives on 2008-12-31
you have to set the CMOS to boot USB first

---

### Post by egrpioneer on 2008-12-31
Thanks for responding! The bios/cmos doesn't indicate USB.

---

### Post by egrpioneer on 2008-12-31
Thanks for taking your time to respond! Since I'm so new to Ubuntu, I can't recall how I handled the disable boot loader situation.

---

### Post by albinootje on 2008-12-31
> **egrpioneer said:**
> Please help me boot into Ubuntu. Set bios for FDD first drive, but no action.

hardware: Toshiba Satellite A10 laptop. ASCI Bios 1.3


How did you install Ubuntu on that external usb hard disk ? On the same machine ? Does it boot properly on other machines ?

I've had trouble on various machines to boot at all from usb-stick or usb-disk with well working installations, which would boot fine on other machines.

---

### Post by dtrot55 on 2008-12-31
I don't know if this would fix your issue..i had a somewhat similar problem until i went into the bios and setup my Large Disc Access to "Other" this allowed for the hard drive geometry to be something linux would unerstand...before i changed that i would just get black screens

---

### Post by egrpioneer on 2009-01-01
Thanks for responding. I used the same laptop to load 8.10 from the CD onto the USB FDD. I haven't tried it on my desktop PC because my first try at at a boot resulted in a Grub 21 error. I don't want to risk that on the PC.

---

### Post by egrpioneer on 2009-01-01
Thanks for responding! My bios doesn't have the large disk access feature.

---

### Post by albinootje on 2009-01-01
> **egrpioneer said:**
> Thanks for responding! The bios/cmos doesn't indicate USB.

I just looked up the specifications for your laptop, I cannot believe that a laptop like that cannot boot from usb.
Can you try the "boot menu", on other laptops it's usually F12 for a boot menu. 
There's a chance that the usb device will show up there.

---

### Post by egrpioneer on 2009-01-01
> **albinootje said:**
> I just looked up the specifications for your laptop, I cannot believe that a laptop like that cannot boot from usb.
Can you try the "boot menu", on other laptops it's usually F12 for a boot menu. 
There's a chance that the usb device will show up there.
Thanks for checking the laptop spec. I just restarted this laptop opened F12, but no USB icon, or USB direction was indicated,

---

### Post by egrpioneer on 2009-01-02
I'm still not able to boot from the external USB-HDD. I overlooked mentioning in this thread that the initial attempt at the installation resulted in a grub 21, error. I fixed it by booting from the XP-Pro CD, and running FIXMBR.
Also, while running Ubuntu live CD, the USB-HDD is shown on the desk top.
I'm determined to work through the issue, but obviously need expert troubleshooting.
Thanks in advance!

---

### Post by caljohnsmith on 2009-01-02
How about posting the output of the following script so we can get a better picture of your setup:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by egrpioneer on 2009-01-02
Thanks x 2! I'll work on this and post the result!!

---

### Post by egrpioneer on 2009-01-02
I ran the script in terminal, but output indicated - resolving home.comcast.net... failed: name or srevice not known
wget: unable to resolve host address 'home.comcast.net'

---

### Post by caljohnsmith on 2009-01-02
> **egrpioneer said:**
> I ran the script in terminal, but output indicated - resolving home.comcast.net... failed: name or srevice not known
wget: unable to resolve host address 'home.comcast.net'
OK, so it doesn't sound like you had internet connectivity when you ran those commands, or at least you are having DNS problems. How about instead right-clicking [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your browser, choose "save target as...", save the script, transfer it to your Ubuntu desktop, and then do:
```
sudo bash ~/Desktop/boot*.txt
```
And see if that works, or let me know if you run into problems again.

---

### Post by egrpioneer on 2009-01-02
I was running Ubuntu live cd on the laptop which was not connected to my wireless network. This communication is running on my desktop which is on the network. Should I open Ubuntu on the PC, and if so, how will Ubuntu see my network connection?

---

### Post by caljohnsmith on 2009-01-02
> **egrpioneer said:**
> I was running Ubuntu live cd on the laptop which was not connected to my wireless network. This communication is running on my desktop which is on the network. Should I open Ubuntu on the PC, and if so, how will Ubuntu see my network connection?
Can you download the script to your desktop computer, and then transfer the file to your Ubuntu desktop while you are running the Live CD, maybe by USB stick or by floppy?

---

### Post by egrpioneer on 2009-01-02
> **caljohnsmith said:**
> Can you download the script to your desktop computer, and then transfer the file to your Ubuntu desktop while you are running the Live CD, maybe by USB stick or by floppy?

I don't have USB stick, or floppy, but could save the output in a notepad attachment and burn a CD and copy it to the next post. Will that work? If so, please advise code needed to get what you need.
Thank you!!

---

### Post by caljohnsmith on 2009-01-02
> **egrpioneer said:**
> I don't have USB stick, or floppy, but could save the output in a notepad attachment and burn a CD and copy it to the next post. Will that work? If so, please advise code needed to get what you need.
Thank you!!
It sounds like that would work, and you might want to use a CD-RW so you don't have to waste an entire CD on the output though. Try following the steps from post #16 to run the script, or let me know if you have problems.

---

### Post by egrpioneer on 2009-01-02
> **caljohnsmith said:**
> It sounds like that would work, and you might want to use a CD-RW so you don't have to waste an entire CD on the output though. Try following the steps from post #16 to run the script, or let me know if you have problems.

OK, thanks, I'll get to work!!

---

### Post by egrpioneer on 2009-01-02
> **egrpioneer said:**
> OK, thanks, I'll get to work!!

I just ran sudo bash ~/Desktop/boot*.txt, but output indicated "no such file or directory"

---

### Post by caljohnsmith on 2009-01-02
> **egrpioneer said:**
> I just ran sudo bash ~/Desktop/boot*.txt, but output indicated "no such file or directory"
OK, for that command to work, you need to make sure you have the "boot_info_script.txt" file saved to your Ubuntu desktop before running that command. If you do:
```
ls -l ~/Desktop
```
That will show you a list of the files on your Ubuntu desktop, and it should list "boot_info_script.txt" as one of them. If not, you still need to transfer that script to your Ubuntu desktop. Also note that commands and file names are case-sensitive, so please make sure you save the file as "boot_info_script.txt" and don't use any upper-case characters to avoid confusion at this point.

---

### Post by egrpioneer on 2009-01-02
> **caljohnsmith said:**
> OK, for that command to work, you need to make sure you have the "boot_info_script.txt" file saved to your Ubuntu desktop before running that command. If you do:
```
ls -l ~/Desktop
```
That will show you a list of the files on your Ubuntu desktop, and it should list "boot_info_script.txt" as one of them. If not, you still need to transfer that script to your Ubuntu desktop. Also note that commands and file names are case-sensitive, so please make sure you save the file as "boot_info_script.txt" and don't use any upper-case characters to avoid confusion at this point.

I just ran 1s -1 ~/Desktop and output indicated bash: 1s: command not found

---

### Post by caljohnsmith on 2009-01-02
> **egrpioneer said:**
> I just ran 1s -1 ~/Desktop and output indicated bash: 1s: command not found
Those are both lowercase Ls, not ones. :)

---

### Post by sadaruwan12 on 2009-01-02
Hi,
Just run this command and tell me the out put
```
ls -l
```
or
```
ll
```

---

### Post by egrpioneer on 2009-01-02
> **caljohnsmith said:**
> Those are both lowercase Ls, not ones. :)

Ah, minor detail. I just ran it and output indicated:
Examples -> /usr/share/example-content
ubiquity-gtkui.desktop

Please advise next step(s)
Thank you!

---

### Post by egrpioneer on 2009-01-02
> **sadaruwan12 said:**
> Hi,
Just run this command and tell me the out put
```
ls -l
```
or
```
ll
```

ls -1
desktop, documents, music, pictures, public, templates, videos

ll: command not found

Thank you!

---

### Post by egrpioneer on 2009-01-03
I'm still stuck with the no boot from external USB-HDD issue.

---

