---
title: "Can't boot into windows vista!"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by Yvan300 on 2009-03-01
Hello i have a dell inspiron 1501 with a dual boot set up with windows vista ultimate and Ubuntu 8.1. I use the Grub boot loader but when i select windows vista from the boot list an error appears saying please remove disks or media and press any key to restart. What does this mean? Ubuntu works fine. What should i do? Oh yeah also i recently deleted my recovery partition. It was located to the left of the C drive, thus i could not use the space for extending the c drive. I then reformatted it in fat 32, could this be causing the problem, help me, i really need my windows partition right now!

---

### Post by caljohnsmith on 2009-03-01
In order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Yvan300 on 2009-04-10
Forget it, i just ended up deleting vista and keeping ubuntu :) Happy i made that decision.

---

### Post by lisati on 2009-04-10
> **Yvan300 said:**
> Hello i have a dell inspiron 1501 with a dual boot set up with windows vista ultimate and Ubuntu 8.1. I use the Grub boot loader but when i select windows vista from the boot list an error appears saying please remove disks or media and press any key to restart. What does this mean? Ubuntu works fine. What should i do? Oh yeah also i recently deleted my recovery partition. It was located to the left of the C drive, thus i could not use the space for extending the c drive. I then reformatted it in fat 32, could this be causing the problem, help me, i really need my windows partition right now!
Welcome to Ubuntu.

Deleting the recovery partition isn't always a good idea - some warranties assume that you have the original OS installed on your computer. I hope you made a backup first or have some other way of reinstalling Vista should the need arise. Whether or not that will happen is a matter of opinion.

I've only ever had a warning message like the one you describe when I've booted from floppy or CD to install or change something.

> **Yvan300 said:**
> Forget it, i just ended up deleting vista and keeping ubuntu :) Happy i made that decision.
Again, welcome to Ubuntu. I hope your experience is relatively painless - there will always be someone at the forums if you want to ask more questions. But please be patient: not everyone's system or preferences are the same, and we might not be able to come up with answers immediately.

By the way, how did you get on with caljohnsmith's suggestion?

---

### Post by Yvan300 on 2009-04-10
Well right now, i have come a long way from this incident, i even applied for the beginners team, and yes i do have a reinstallation disk for vista, incase i need it. But i have learned that ubuntu is the way to go and have ported a lot of my friends to this wonderful OS. Glad i found it :)

---

### Post by drowner on 2009-04-10
> **Yvan300 said:**
> Well right now, i have come a long way from this incident, i even applied for the beginners team, and yes i do have a reinstallation disk for vista, incase i need it. But i have learned that ubuntu is the way to go and have ported a lot of my friends to this wonderful OS. Glad i found it :)

Deleting windows was the best thing I ever did.

Until then I used to resort to windows to do things I just couldn't get linux to do, like sync my ipod, watch some vids on the internet and so on....

Then I deleted the windows partition, worked at the things I couldn't do - and now they all work, no problems.

All the best.

---

### Post by AXeS on 2009-04-10
im still struggling.

net and music


trying my best to get it sorted.

congrats to the c0nvert Yvan300.

---

### Post by Yvan300 on 2009-04-11
Yeah, when switching to ubuntu you always think that you can't do something that you could have done in windows, but with a little tinkering and a bit of help from the forums, ubuntu will beat vista anyday :)

---

