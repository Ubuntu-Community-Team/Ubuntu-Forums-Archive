---
title: "Wifi is hard switched off."
date: 2014-11-11
forum: Networking &amp; Wireless
---

### Post by recon2 on 2014-11-11
I do not have a wifi switch on my computer, yet it still says it is hard switched off in the console? I can't get a wired connection because my Lenovo doesn't have one.
Running Ubunty 12.04
I am using a StormFly, a USB wristband running Ubuntu.

Lenovo Yoga 2

---

### Post by jeremy31 on 2014-11-11
Try ```
sudo modprobe -r ideapad_laptop
``````
sudo rfkill unblock all
```
If it works now, then ```
echo "blacklist ideapad_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by recon2 on 2014-11-11
I did the first 2 commands. I did the rfkill list, only my bluetooth was there. Not even wifi anymore. Restarting.

Just restarted. Absolutely no change. Back to were I started. Urgent halp! D:

---

### Post by jeremy31 on 2014-11-11
Run the wireless script and post the wireless-info file that should be in the /home folder```
[COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```[/FONT][/COLOR]

---

### Post by recon2 on 2014-11-11
Failed , name or service not known, Unable to resolve host address 'dl.dropbox.com'

---

### Post by coffeecat on 2014-11-11
> **recon2 said:**
> I can't get a wired connection because my Lenovo doesn't have one.

Are you absolutely sure? Perhaps Lenovo don't include ethernet ports in some of their machines, but I had a tiny netbook of another make and it was a year before I discovered the ethernet port hidden under a neat little dust cover.

Anyway, running a wget command with no internet access won't work. Have a look at this post:

[http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385)

Method 2 is what you need to be able to download the wireless script on another system and then transfer it to your Ubuntu system to run.

---

### Post by jeremy31 on 2014-11-11
> **recon2 said:**
> I do not have a wifi switch on my computer, yet it still says it is hard switched off in the console? I can't get a wired connection because my Lenovo doesn't have one.
Running Ubunty 12.04
I am using a StormFly, a USB wristband running Ubuntu.

Lenovo Yoga 2

Missed the part about using 12.04.  The wifi card in the Lenovo is likely too new to be supported by 12.04 and will need backported drivers
```
lspci -nnk | grep -iA2 net
```
Do you have issues with 14.04 on the Lenovo?

---

### Post by recon2 on 2014-11-11
I did that, it spit out " Inge Corperation Deviece" thanks

---

### Post by jeremy31 on 2014-11-11
> **recon2 said:**
> I did that, it spit out " Inge Corperation Deviece" thanks

Can you be more specific, my laptop shows ```
01:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lenovo Device [17aa:3218]
    Kernel driver in use: ath9k

```

It would be nice to have the numbers inside the brackets on the first line and second line as they are important

---

### Post by coffeecat on 2014-11-11
@recon2, to get the complete terminal output into your post, and without typos, you can highlight the output in the terminal with the mouse, then right-click -> copy, and then paste into your post. Please use code tags the way you see them in jeremy31's post, like this:

[noparse]```
terminal output
```[/noparse]

Appears like this when posted:

```
terminal output
```

---

### Post by recon2 on 2014-11-11
I cant use internet, how am I supposed to get the code from deviece to deviece with out errors from my typos?

---

### Post by coffeecat on 2014-11-11
> **recon2 said:**
> I cant use internet, how am I supposed to get the code from deviece to deviece with out errors from my typos?

Paste into a text editor. Save as a text file. Copy file to a USB flash drive. Transfer to the machine you are posting from... I think you get the picture. It's important to provide the whole of the terminal output and you don't want to be copying that by hand.

---

### Post by recon2 on 2014-11-11
ZHow do I get it froma  deviece that doesnt have any internet at all? without typing it which would most certainly contain typos?

---

### Post by chili555 on 2014-11-11
> **recon2 said:**
> I cant use internet, how am I supposed to get the code from deviece to deviece with out errors from my typos?We will not be able to help you if we haven't any idea what your details are. All of us know, from previous experience, that some Yoga 2s have a problem with the wireless switch. You posted your *rfkill* result and that doesn't seem to be the issue. Therefor, we wonder if your wireless device has a required driver.

All we can suggest is that you write down the terminal output on a piece of paper and proofread it carefully twice and post it here. Proofread your posting carefully twice, too, before you click 'Submit Reply.'

---

### Post by coffeecat on 2014-11-11
> **recon2 said:**
> ZHow do I get it froma  deviece that doesnt have any internet at all? without typing it which would most certainly contain typos?

I have already told you how to do this in the previous post. **Please** read this.

---

### Post by recon2 on 2014-11-11
my first reply didnt show up on my screen. Sorry!

---

### Post by jeremy31 on 2014-11-11
> **recon2 said:**
> my first reply didnt show up on my screen. Sorry!

No problem, all we need is the info from ```
lspci -nnk | grep -iA2 net
``` that is between the brackets [????:????] on the first 2 lines

I still think Ubuntu 14.04 is a better choice as the correct drivers should be there unless you see (rev cb) in the lspci command as I think you likely have an Intel 7260 wifi card

Please ignore the smiley inside the brackets, that is one thing that can happen without using the code tags

---

### Post by recon2 on 2014-11-11
I'll get on the numbers, I can't update to ubuntu 14.04 until I get my internet fixed. Thanks :)

---

