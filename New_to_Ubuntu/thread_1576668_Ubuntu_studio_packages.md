---
title: "Ubuntu studio packages"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by itsvan on 2010-09-17
Hi im currently running Ubuntu Lucid,i have a question..is it possible to install the same programs that Ubuntu studio has but without upgrading or reinstalling Ubuntu studio over Lucid? for example i want to install the video or audio programs it comes with, can i do it without doing anything to my current installation?

---

### Post by davidmohammed on 2010-09-17
open-up synaptic manager or software-center and search for ubuntustudio-desktop  - install the suggested packages.

---

### Post by ubunterooster on 2010-09-17
Sure, just put the name of the program into synaptic. You can even get the artwork, desktop setup, and menu of of ubuntustudio there :D

Edit: or like David said

---

### Post by amjjawad on 2010-10-02
I installed UbuntuStudio 10.04 but by mistake, I didn't choose the softwares from the list given during setup/installation. I'm aware that I could download whatever I like but problem is, my internet connection is too slow. Is there anyway I could get these programs/softwares after installation? I have the DVD (UbuntuStudio 10.04 32-bit) but not sure what to do?

Shall I just insert my DVD and do something to install these softwares or any command maybe?

Thank you!

---

### Post by ubunterooster on 2010-10-02
Open the the Synaptic Package manager. Go to edit>sources. Enable the CD repository and stick the CD in

---

### Post by amjjawad on 2010-10-02
> **ubunterooster said:**
> Open the the Synaptic Package manager. Go to edit>sources. Enable the CD repository and stick the CD in

Thanks :)
Will try that and hope it will work.

I was surprised that there was no graphical installation like Ubuntu for example. Didn't pay attention to the bottom where it says "Space to select".

---

### Post by ubunterooster on 2010-10-02
Let us know if it works for you :D

---

### Post by amjjawad on 2010-10-02
> **ubunterooster said:**
> Let us know if it works for you :D

I had a problem with Ubuntu Studio :( that's why I had to install Ubuntu 10.04 yet again. I've been trying lots of OS's lately (Fedora, OpenSUSE, Kubuntu, etc) and so far, I didn't feel much comfortable except with Ubuntu.

The problem with some of these OS's was my Wireless Card. Some OS's like OpenSUSE, Open Solaris and Ubuntu Studio couldn't detect the driver. It's a long story so I don't want to disturb anyone with it :)

Thank you so much for help :)

Oh yes, I think I read it some where but I can't remember where?
**[COLOR=Blue]Is it possible to use Ubuntu Studio's DVD to install the same software in Ubuntu 10.04?[/COLOR]** Ubuntu 10.04 runs very smoothly and I really like it more than the other OS's.

---

### Post by ubunterooster on 2010-10-02
stick the CD in and go to synaptic and add the CD to the source list as before. then run ```
sudo apt-get install ubuntustudio-desktop
``` :D

---

### Post by amjjawad on 2010-10-02
> **ubunterooster said:**
> stick the CD in and go to synaptic and add the CD to the source list as before. then run ```
sudo apt-get install ubuntustudio-desktop
``` :D

Okay, I don't have "source" under Edit, there's "Add CD-ROM..." and when I click on it, it starts loading something but nothing will appear on the package panel on the right.
Just to be very clear, all what I'm trying to do is to install the same "softwares" from Ubuntu Studio into Ubuntu 10.04 ... that's all :)

The command that you posted, I have a feeling it's used to install Ubuntu Studio instead of its softwares :P

---

### Post by ubunterooster on 2010-10-02
the command will add all Ubuntu Studio packages to regular Ubuntu, but only if it has the CD recognized as an added source.

I hope I'm making sense, I had a hard long, frustrating day

---

### Post by iMisspell on 2010-10-03
> **itsvan said:**
> Hi im currently running Ubuntu Lucid,i have a question..is it possible to install the same programs that Ubuntu studio has but without upgrading or reinstalling Ubuntu studio over Lucid? for example i want to install the video or audio programs it comes with, can i do it without doing anything to my current installation?
Two weeks have past so im sure you have what you want, but for others interested:
[https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList)
Has a list with alittle info about each program.

_

---

### Post by amjjawad on 2010-10-03
> **ubunterooster said:**
> the command will add all Ubuntu Studio packages to regular Ubuntu, but only if it has the CD recognized as an added source.

I hope I'm making sense, I had a hard long, frustrating day

1- Synaptic Package Manager 
2-Edit
3- Add CD-ROM ...
4- Error message : "E: Failed to mount the cdrom."

:(

---

### Post by ubunterooster on 2010-10-04
Was the CD mounted so you could see it on your desktop?

---

### Post by amjjawad on 2010-10-04
> **ubunterooster said:**
> Was the CD mounted so you could see it on your desktop?

Yes, it was.
Above all, once I put the DVD, Synaptic Package Manager will pop up but when I go to Edit > Add CD-ROM ... and click on it, I got that error message.

---

### Post by ubunterooster on 2010-10-04
:( I have no idea why it would be doing that.

---

### Post by amjjawad on 2010-10-04
It's ok, ubunterooster :)

Anyone has an idea how to do it?
All what I need to do is: Install the softwares in Ubuntu Studio's DVD into Ubuntu 10.04.

Thank you :)

---

