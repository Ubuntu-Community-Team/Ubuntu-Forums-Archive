---
title: "arrrggg windows"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by VonZapper on 2009-07-15
So due to a nasty little virus I installed Ubuntu in order to save all the important things on the computer, and I liked it so much I ended up giving it the full install it deserves.

Now the problem is that I need to install windows because my wife has work stuff that isn't Linux friendly.

I know there was a way to set up Linux as a second load prompt if you had windows on the system, but is there a way to load windows as the second option when Ubuntu is fully installed on the pc.

If there is a way can someone please show me how since I'm obviously "challenged" is this field.

Thanks.

---

### Post by mano cazalet on 2009-07-15
if I got it right, you want to install windows with ubuntu already installed, right?

[here]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm") is a great guide to do that.

---

### Post by nhasian on 2009-07-15
Hello,

you have two choices I think.  you could:

1)  resize one of the ubuntu ext3 or ext4 partitions to make room for Windows.  then boot off the windows DVD to install into the empty partition (be careful not to format any of your ubuntu partitions).  If you do this then the NTLDR will overwrite grub so you will have to fix that to get back into ubuntu.

[http://www.supergrubdisk.org/w/index.php5?title=Howto_Fix_Grub](http://www.supergrubdisk.org/w/index.php5?title=Howto_Fix_Grub)

2) you can install Virtualbox and then load Windows inside of a virtual computer.  so windows will load within an ubuntu window.  you can even make it fullscreen and you wouldnt notice the difference.... as long as your not playing any 3d games in windows this will be a good choice.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by n8bounds on 2009-07-15
I recommend the Vbox solution. Very clean, and doesn't muck up your uptime (your right to gloat over after 380+ days as a Linux user)! :)

---

### Post by H2SO_four on 2009-07-16
> **mano cazalet said:**
> if I got it right, you want to install windows with ubuntu already installed, right?

[here]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm") is a great guide to do that.

That is a good way to do it.  I had just Linux for a while and needed to get windows installed.  I installed using that method.

---

### Post by CompizDoDo on 2009-07-16
i think doing VBox is the best way theres always the other option of getting an external hdd and booting windows onto that

---

### Post by VonZapper on 2009-09-09
> **mano cazalet said:**
> if I got it right, you want to install windows with ubuntu already installed, right?

[here]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm") is a great guide to do that.



So I tried this way (changed the option from vista to XP)  but when I went to install windows my list of partitions is empty.  When I pressed Enter to install in a new partition I got the good old blue screen.  Anyone ever come across this before?

I'm going to try Virtubox next.

---

### Post by The Judderman on 2009-09-09
Hiya!

I'd also go with VBox, but just be aware that if you got Windows as an OEM (ie, came preinstalled on your computer), it might not work in VBOX. I have an ASUS laptop, and the OEM restrictions mean that it doesn't seem to recognise that the virtual box is the same laptop as the original and won't load... Just for info

(i have managed this fine with other OEMs on different laptops and it worked a dream!)

The Judderman

---

### Post by starcannon on 2009-09-09
I've been able to repurpose my obsolete oem licenses by using a generic install disc, and then reregistering using MS's automated process after installation is complete. All nice and legal, and tidy; and beats throwing a perfectly good license in the trash.

> **The Judderman said:**
> Hiya!

I'd also go with VBox, but just be aware that if you got Windows as an OEM (ie, came preinstalled on your computer), it might not work in VBOX. I have an ASUS laptop, and the OEM restrictions mean that it doesn't seem to recognise that the virtual box is the same laptop as the original and won't load... Just for info

(i have managed this fine with other OEMs on different laptops and it worked a dream!)

The Judderman

---

