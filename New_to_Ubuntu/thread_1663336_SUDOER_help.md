---
title: "SUDOER help"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by wats6831 on 2011-01-09
Hi, I'm VERY new to Linux. I spent at least two hours last night trying to edit my sudoer in order to give myself admin and NOT require me to input the root password every time i need to do something. 

So what i did was: 

su root

sudo visudo

Then i added the two lines that begin with my username casey

 /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
Casey   ALL=(ALL) ALL
# Allow members of group sudo to execute any command

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
Casey   ALL=(ALL) ALL
# Allow members of group sudo to execute any command




My question is: What do I add or how do I make it so that I have all privledges and also where and how do I add the NOPASSWD: ALL

I've tried about every concievable combination and it either isn't effective or I get a syntax error when i try to save the file. 

I've tried several different ways I found on google and none of them work. As soon as I go to add a software package I'm prompted for the root password. I want to be able to learn and do things on this system without having to input a password 1,000 times a day. 

I know this is VERY basic but I'm really frustrated as i tried every way I could find on the internet. 

Thanks for any help.

---

### Post by cariboo on 2011-01-09
In the amount of time you've spent trying to make your system work like Windows, you could have used sudo several thousnad times. That being said, have a look at [this]("https://help.ubuntu.com/community/RootSudo") document, it will help you solve your problem. The information you need is at the bottom of the page. I would suggest you read the whole page, before making any changes.

---

### Post by oldos2er on 2011-01-09
Once you get your sudoers file sorted out, use **sudo -i** to give yourself a persistent root terminal.

---

