---
title: "Mounting my Windows hard drive"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by endlessmike on 2008-12-09
Hi. I know there are about 1,000,000 posts similar to this and i tried to follow them to no avail.

Anyway, I want use Ubuntu to retrieve files from my crashed HP. It randomly crashed trying to emerge from hibernation. So anyway, I am not that good with computers beyond uhhhhh..... OK I'm not that good. 

I tried the 
sudo mkdir /media/windows

then the sudo mount -t ntfs /dev/hda1/ media/windows
where it tells me No such file or directory.

I would guess my hard drive is in some sort of working order as it lets me save openoffice documents.  

When i try to access to harddrive under the PLaces tab it gives me a DBus error:Noreply


can someone talk me through this?

Thanks!

---

### Post by endlessmike on 2008-12-09
OK, I did sudo fdisk -l and i believe the windows is "sda1"
i tried this and not an input/out error stating ntfs is inconsistent, hardware faults, or have Softraid/fakeraid hardware. It tells me to run chkdsk /f. What is that/where do i do that?

---

### Post by oilchangeguy on 2008-12-09
> **endlessmike said:**
> Hi. I know there are about 1,000,000 posts similar to this and i tried to follow them to no avail.

Anyway, I want use Ubuntu to retrieve files from my crashed HP. It randomly crashed trying to emerge from hibernation. So anyway, I am not that good with computers beyond uhhhhh..... OK I'm not that good. 

I tried the 
sudo mkdir /media/windows

then the sudo mount -t ntfs /dev/hda1/ media/windows
where it tells me No such file or directory.

I would guess my hard drive is in some sort of working order as it lets me save openoffice documents.  

When i try to access to harddrive under the PLaces tab it gives me a DBus error:Noreply


can someone talk me through this?

Thanks!

the easiest way to do it, would be to remove the drive. set the jumper to slave, and install it as a second drive in another computer with windows. then you can see and save your files to either that computer, or a usb thumb drive, or whatever.

---

### Post by oilchangeguy on 2008-12-09
> **endlessmike said:**
> OK, I did sudo fdisk -l and i believe the windows is "sda1"
i tried this and not an input/out error stating ntfs is inconsistent, hardware faults, or have Softraid/fakeraid hardware. It tells me to run chkdsk /f. What is that/where do i do that?

you'll have to boot from your windows cd. and follow the prompts to enter the recovery console. then type chkdsk /f

---

### Post by endlessmike on 2008-12-09
> **oilchangeguy said:**
> you'll have to boot from your windows cd. and follow the prompts to enter the recovery console. then type chkdsk /f
so in the same manner i would run a chkdsk /r?
sorry for being dense.

---

### Post by oilchangeguy on 2008-12-09
> **endlessmike said:**
> so in the same manner i would run a chkdsk /r?
sorry for being dense.

you are correct.

---

### Post by endlessmike on 2008-12-09
It says chkdsk /f is not valid.

---

### Post by oilchangeguy on 2008-12-09
> **endlessmike said:**
> It says chkdsk /f is not valid.

from my computer right click on the hard drive, properties, tools, error checking. select both boxes, yes at next restart. and restart the computer.

---

### Post by endlessmike on 2008-12-09
> **oilchangeguy said:**
> from my computer right on the hard drive, properties, tools, error checking. select both boxes, yes at next restart. and restart the computer.

i can't get into that. It loops from the we are sorry for the inconvenience screen, windows didn't shut down properly back then it will go to the windows status bar then to restarting itself. I cannot open it in safe mode, command prompt, etc.

Some one mentioned to me an "Ultimate Boot CD" is this recommended?

---

### Post by theozzlives on 2008-12-09
> **endlessmike said:**
> Some one mentioned to me an "Ultimate Boot CD" is this recommended?

It' your Windows install CD

---

### Post by oilchangeguy on 2008-12-09
> **endlessmike said:**
> i can't get into that. It loops from the we are sorry for the inconvenience screen, windows didn't shut down properly back then it will go to the windows status bar then to restarting itself. I cannot open it in safe mode, command prompt, etc.

Some one mentioned to me an "Ultimate Boot CD" is this recommended?

i've never used it. even if it works, looks like you've got other problems. you might want to think about what i suggested in post #3. get your data, and do a fresh install of windows.

---

### Post by oilchangeguy on 2008-12-09
> **theozzlives said:**
> It' your Windows install CD

????????????????????????????????????????????????????????????????

---

### Post by endlessmike on 2008-12-09
I tried to run a chkdsk /r earlier but it was unable to finish.

---

### Post by oilchangeguy on 2008-12-09
> **endlessmike said:**
> I tried to run a chkdsk /r earlier but it was unable to finish.

just get your data, if you can. and reinstall windows.

---

### Post by endlessmike on 2008-12-09
> **oilchangeguy said:**
> i've never used it. even if it works, looks like you've got other problems. you might want to think about what i suggested in post #3. get your data, and do a fresh install of windows.

That makes sense to the limited amount of understanding i have, but i have no clue on how to do that nor the resources. I am trying to do this myself as I have lost my job (yay recession) and I was told it would cost 50 bucks for someone to do it. Plus I have alot of files relating to my unemployment with personal information that i don't trust people with.

---

