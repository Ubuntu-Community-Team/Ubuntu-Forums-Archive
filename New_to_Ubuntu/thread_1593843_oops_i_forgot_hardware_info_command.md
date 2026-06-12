---
title: "oops i forgot hardware info command"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by flyingsliverfin on 2010-10-11
sorry ive completely forgotten... whats the terminal command that gives me how much memory i have,what my cpu is and how many ghz, and how much vram i have?

thx

---

### Post by wkhasintha on 2010-10-11
command is **lshw** 

here are few additional commands serves similar purposes.

**free -m** = free memory
**du -ahc** = disk usage

---

### Post by oldfred on 2010-10-12
You can directly convert to HTML and open in firefox:

HTML version of info (corrected)
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html

Or text:
sudo lshw >hw.txt
 udevadm info --export-db > file.txt

sudo dmidecode --type bios
sudo dmidecode >bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.

---

### Post by yetiman64 on 2010-10-12
> **oldfred said:**
> You can directly convert to HTML and open in firefox:

HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox [COLOR=Red]/hardware_info.html[/COLOR]....

@ oldfred, great idea this, but you're missing a tilde symbol (~) before the second instance of "[COLOR=Red]/hardware_info.html[COLOR=Black]" (colour for highlighting only). cheers from yetiman64.[/COLOR][/COLOR]

---

### Post by oldfred on 2010-10-12
Thanks,    	yetiman64.

I went back in my notes to check and it has the extra tilde. I normally copy & paste my notes as I do not alway remember all the details.

I will edit the original entry just for posterity in case some one copies it.

---

### Post by yetiman64 on 2010-10-12
> **oldfred said:**
> Thanks, yetiman64....
You're most welcome oldfred :)

> **oldfred said:**
> .... in case some one copies it. Yeah, like this old mug (me) :lol:. btw I like the ability of lshw to output to html like that, that's a very handy hint of yours for me to use (hence the test of it) - much appreciated.

---

### Post by flyingsliverfin on 2010-10-13
thanks.
i like the html display a lot better than just the plain test :)

---

