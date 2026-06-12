---
title: "system held"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by coolspot3 on 2010-03-19
My system helds during working and i just restart to get it refresh. can anybody tell me how to refresh the system without restarting? please tell me as soon as possible.

---

### Post by luctor on 2010-03-19
Can't you just log out and log in again ?

---

### Post by coolspot3 on 2010-03-20
> **luctor said:**
> Can't you just log out and log in again ?
Actually when my system gets stuck, I have to restart the system again, all the applications become unresponsive and i lost all of my data at once by restarting computer.. 
 How can I log out and then log in when none of the application is responding

---

### Post by The Real Dave on 2010-03-20
If you type Ctrl+Alt+F1 you'll be droppped into a command line. 

Type your username, then hit enter. Then type your password (you won't be able to see it going in, but it is) and hit enter again, and you've logged in :)

Now type 

```
sudo reboot
```

and hit enter. Give it your password again, hit enter, and your computer will begin rebooting cleanly. 

Depending on how locked up your computer is though, you might not be able to do that. A hard reboot may be the only option.

You might want to give some more information about the type of problem, so that we can help solve it, so that your computer doesn't lock up again :)

---

### Post by coolspot3 on 2010-03-20
Hi, thanx for telling me. I will try it and then tell you what happened.... But how to get out of this command line? will it restart? or Do I have to do it manually? 
Apparently it seems no problem. systems starts smoothly, work intelligently and then at once when some new file is being opened, or closed or web browser is being closed or open, system gets stuck. In the meanwhile the mouse is the only thing which moves around but all other buttons apear nonresponsive.

My system specs are:
ram 256mb
processor 1.5Hz
Hard Disk: 80 GB
I dont know about make names

Might this information help u find out the actual problem....
Cheers & thanx

---

### Post by The Real Dave on 2010-03-20
Yup, after you follow the above, the computer will reboot.

I think I see your problem. 256Mb of RAM isn't much for a standard Ubuntu install. It would probably be a good idea to look into 'lighter' alternatives, such as [Xubuntu]("http://www.xubuntu.org").

---

### Post by coolspot3 on 2010-03-21
O Thanx,
I il do the task..

---

### Post by coolspot3 on 2010-03-27
Hi,
 I Have re tried the sudo reboot.
For two three days it worked normally, but now still creating the same problem. Its ram is also changed to 1 GB now. But the problem is there. can u please tell me any command that can unlock the system without restarting it? and without closing all the programs and applications?
Please help me, I am in so much trouble.

---

### Post by s_ø on 2010-03-28
Hi.
Press Ctrl + Alt + Backspace to kill the x-server, and get a new login screen. You might need to enable the shortcut

From [http://www.ubuntugeek.com/how-to-enabledisable-ctrlaltbackspace-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-enabledisable-ctrlaltbackspace-in-ubuntu-9-10-karmic.html)
[B]
Using GNOME[/B] * Get to the System->Preferences->Keyboard menu.
 * Select the “Layouts” tab and click on the “Layout Options” button.
 * Then select “Key sequence to kill the X server” and enable “Control + Alt + Backspace”.




But as the poster wrote, post some more details about the crashes so we can help try to fix it.

---

