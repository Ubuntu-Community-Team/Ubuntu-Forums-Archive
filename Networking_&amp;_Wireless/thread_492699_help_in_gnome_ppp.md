---
title: "help in gnome ppp???"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by nooor7772000 on 2007-07-05
help in gnome ppp??? 

--------------------------------------------------------------------------------
[SIZE="4"]
hi i try conect to usb modem by nokia 6630 in ubuntu and it work well in windows well by these setting,,,,,,,,how can i apply these setting specilly the bold written in gnome ppp well to make it work ......i want apply all these setting to get it work as nothing from previous posts help me in..............[/SIZE]


Configure the Modem:

- Choose 115200 from the Maximum Port Speed drop-down menu
- Select Advanced tab, enter the following into the Extra initialization commands field: **AT+CGDCONT=1,"IP","MOBINILWEB"**- Select Change Default Preferences and **change the Flow Control field to read None**

Dial-up Networking Set-up:
- Enter the relevant telephone number:
***99# **for most GPRS handsets

- From the Modem Configuration select 115200 as the maximum speed (bps)
[B]- Tick Enable hardware flow control
- Un-tick Enable modem error control
- Un-tick Enable modem compression
- Un-tick Enable modem speaker[/B]
-
**- Un-tick Use dialing rules.**

- **Untick Use IP Header compression**

---

### Post by dfreer on 2007-07-05
Hi,

  Am I understanding correctly that you are trying to access the internet from ubuntu using a bluetooth connection to your nokia 6300? Where was the original guide that you copy + pasted this excerpt from?
The how to you already posted in ( [http://ubuntuforums.org/showthread.php?t=257091](http://ubuntuforums.org/showthread.php?t=257091) ) seems to be a well written guide, if you are following that guide what part are you specifically having trouble with? 


Several things:
(1). Try not make multiple threads about the same subject, as it makes it hard for people to help you. If nothing else, bump a thread before creating a new one. Here's all of the duplicate threads I found:

Also about nokia 6630 modem:
[http://ubuntuforums.org/showthread.php?t=479395](http://ubuntuforums.org/showthread.php?t=479395)
[http://ubuntuforums.org/showthread.php?t=483337](http://ubuntuforums.org/showthread.php?t=483337)

About backtrace2 ISO:
[http://ubuntuforums.org/showthread.php?t=467985](http://ubuntuforums.org/showthread.php?t=467985)
[http://ubuntuforums.org/showthread.php?t=462760](http://ubuntuforums.org/showthread.php?t=462760)

(2). Please try to be as clear as possible when asking for help, it makes it hard for people to understand what the problem is. Also stay away from excessive use of .......... ????? and the occasional ,,,,,,,,, :D
Just in general re-read all of your posts and try to be as clear as possible.

---

### Post by nooor7772000 on 2007-07-05
first ..thanks alot for ur reply for me and that is realy kind of and i want to tell u that i did that by mistake as i ask for help i do not know in what forum part or how to do it so i try as i know and i can,,,and i realy firts search and try get help in that but finally i found that i just need help in applying that setting to gnome ppp by these specific data which will work for me and i am useing cable usb not work for bluetooth,,that is all,,,
and thanks again,,,,

---

### Post by nooor7772000 on 2007-07-08
still wait for help

---

