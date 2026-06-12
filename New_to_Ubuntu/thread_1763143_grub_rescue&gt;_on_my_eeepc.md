---
title: "grub rescue&gt; on my eeepc"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by tchoklat on 2011-05-20
I have an EEEPC S101 with Win XP and Ubuntu Net Book 10.10 dual booting on the internal 16gb ssd. I (stupidly) removed the ubuntu partition including the home partition and of course that included grub so on turn on I get;

"grub rescue>" and nothing else.

Windows XP is still intact (I think).

How do I repair the MBR to boot to XP so I can install ubuntu again?

regards and thanks in advance.

tchoklat

---

### Post by Rubi1200 on 2011-05-20
Hi,
you can restore the Windows bootloader using these instructions:
You will need to download and burn an Ubuntu image to a USB stick:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Then run in live mode and enable the universe repository in Software Sources, then these commands in the terminal:

```
sudo apt-get update

sudo apt-get install lilo

sudo lilo -M /dev/sda mbr
```

Installs a basic Windows-style bootloader. Ignore error messages, they are not relevant here as we just want to get it installed to the MBR.

---

### Post by tchoklat on 2011-05-21
Hi,

INstalled Ubuntu on my SD card and started it is live mode, though I find now that my eeepc will not detect my wireless network. Odd as it always has whether I use XP, Ubuntu, or my iPhone. Any idea. I am getting a bit frazzled.

Tony

---

### Post by Rubi1200 on 2011-05-22
First try running the last 2 commands to install lilo without apt-get update and see what happens.

What wireless card do you have?

```
sudo lshw -C network
```

Also, post this output:

```
ifconfig
```

There might be another way to do this as well, but first try what I suggested please.

---

### Post by tchoklat on 2011-05-22
> **Rubi1200 said:**
> First try running the last 2 commands to install lilo without apt-get update and see what happens.


[B]I did this and Lilo is not installed. Am I able to download a lilo deb and install it on my live SD and then continue as you suggest?

Tony[/B]




What wireless card do you have?

```
sudo lshw -C network
```

Also, post this output:

```
ifconfig
```

There might be another way to do this as well, but first try what I suggested please.

[B]
I am not at home, I will post these outputs as soon as I can though the wireless card is standard as supplied on the EEEPC and it works/worked with XP and ubuntu before![/B]

---

### Post by tchoklat on 2011-05-23
Hi,

Got my wireless going and all is fine. Installed MBR and Windoze boots. Thanks for your assistance. What a gr8 community!

Tony

---

### Post by Rubi1200 on 2011-05-23
> **tchoklat said:**
> Hi,

Got my wireless going and all is fine. Installed MBR and Windoze boots. Thanks for your assistance. What a gr8 community!

Tony

Excellent! I am really glad you got this sorted out :-)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

