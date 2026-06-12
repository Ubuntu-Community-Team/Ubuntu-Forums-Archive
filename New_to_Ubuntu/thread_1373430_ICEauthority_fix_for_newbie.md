---
title: "ICEauthority fix for newbie"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by crowdedelevator on 2010-01-05
Ok. Here it goes... I upgraded to 9.10 and I got that issue with not having rights to ICEauthority or whatever. Im not the brightest at this stuff, but this is ridiculous. I've done the safe mode chown thing, and that didn't work. And I also tried something with sudo gedit, and trying to edit a file, but my ubuntu loads choppy and disfunctional. Its turning me off to linux all together. I loved 8.04 although I had pain in the butt issues, but it worked.   This is a pain, and I've been at this for days and nothing the forums say work. I've read (solved) forums that don't answer it, and open ones that don't either.  Im frustrated. Someone email me @ [EMAIL="scottleestewart@tmail.com"]scottleestewart@tmail.com[/EMAIL]  I get instant email, but since its my only way of internet, and its horrid, im saying email please.   Thanks

---

### Post by Methuselah on 2010-01-05
My .IceAuthority is owned by me and my group and has only read/write permissions by owner.

What error are you getting? Is it that .IceAuthority cannot be read?

If it only occurs when you try to log into the desktop then you don't have to boot into recovery mode.
Just hit CTRL+ALT+F2 at the login window to switch to a vt command line and login there (password will not be echoed).

Then

```

sudo chown you:you ~/.IceAuthority

```
where you is your login name

```

chmod 0600 ~/.IceAuthority

```

Then hit ALT+F7 to get back to the graphical login window and try to login there.

If you have to boot into recovery mode (because I misunderstood the extent of the problem) then use /home/you/.IceAuthority for the filename.

This should make your permissions exactly like what exists for me in default Karmic.
I don't see why that would not work but I could be wrong because I have never had any problem with this file.

I understand you're frustrated and you did a good job explaining that but you didn't really provide many details about your problem.
I made by best guess and hope that helps!

---

### Post by crowdedelevator on 2010-01-05
My appologies The error was that of " Could not update .ICEauthority file /home/scott/.ICEauthority"  Then  "There is a problem with configuration server. (/usr/lib/libconf-2-4/gconf-sanity-check-2 exited with status 256)  I looked up forums, some that said to boot in recovery mode, and do chown(I don't understand most entries, but im sure I will one day 8D! ) like this  Recovery-> root prompt->  Chown user:user /home/user/.ICEauthority Chmod 644 /home/user/.ICEauthority  Exit  And a lot of  them saying to reinstall ubuntu 9.10. My partitions are to be  Ext4 mouted as / Ext4 monted as /home And a swap.  I didn't set it up that way, but halfway through helping me out, my family member decided to not return calls so im stuck.  But go easy on me, because im brainless and no nothing of command prompts, which is the point of using ubuntu for me, to learn.

---

### Post by Methuselah on 2010-01-05
So are you in the process of reinstalling now?

---

### Post by crowdedelevator on 2010-01-05
No, I have to set my laptop back up. I reinstalled about 6 times today and was burnt out.  The first partition I have to format, the second has files on it already from my 8.04 ubuntu I had. I will set up my laptop and do as your original post said.  Id really like it if you would email me so I can set up a better way of communicating. Is that fine? You seem to understand my issue

---

### Post by crowdedelevator on 2010-01-05
> **Methuselah said:**
>  
 Just hit CTRL+ALT+F2 at the login window to switch to a vt command line and login there (password will not be echoed).

Then

```

sudo chown you:you ~/.IceAuthority

```where you is your login name

```

chmod 0600 ~/.IceAuthority

```Then hit ALT+F7 to get back to the graphical login window and try to login there.

If you have to boot into recovery mode (because I misunderstood the extent of the problem) then use /home/you/.IceAuthority for the filename.

This should make your permissions exactly like what exists for me in default Karmic.
I don't see why that would not work but I could be wrong because I have never had any problem with this file.



I did this, and  the second error I spoke of, the one about gconf-sanity-check-2 exiting with status 256  Now what? It loads the desktop.... but not really. Its a neon green and pink, in the likes of a snowy tv. So I hit my restart switch on my laptop and it brings up the options menu, so I grab it and move it around the screen to show the background, but there isn't any other items on the screen. This is screwed up....

---

### Post by crowdedelevator on 2010-01-06
Someone PLEASE help me tonight. This ios bugging me. I've been looking up all kinds fo things for this second error and posted about it, w/ no avail. Please help and drop off a quick email.

---

### Post by Methuselah on 2010-01-06
I found a thread with other people experiencing the same gconf error.
A poster claimed to fix it by doing the below:

```

sudo chmod 755 /etc/gconf/gconf.xml.*

```

That will set all gconf.xml.* files to rwxr-xr-x permissions.

Honestly, I do not know what caused your initial problems.
But I'd recommend that when you want to 'sudo' graphical applications that launch in their own windows that you use **gksu** rather than **sudo**.

ie **sudo apt-get install blah** but ***gksu* gedit**.

BTW, I think if you click thread tools at the top you can subscribe to the thread to  get emails when it is updated.
I prefer to respond in the thread so that others can give input as well if they see something they can help with.

---

### Post by crowdedelevator on 2010-01-06
Everything that loaded on google said it was a bug. All I did was install 9.10. But thank you. I didn't know about thread tools. Ill try and see if my cell allows me to click it(its a crappy sidekick 08) and I will let you know if it worked. How did you learn the command line?

---

### Post by Methuselah on 2010-01-06
> **crowdedelevator said:**
> Everything that loaded on google said it was a bug. All I did was install 9.10. But thank you. I didn't know about thread tools. Ill try and see if my cell allows me to click it(its a crappy sidekick 08) and I will let you know if it worked. How did you learn the command line?

Yeah, give it a try (both the subscribing and the fixing of gfconf error).
The first way I learned the command line is the way you are learning it, from what others did.
Then you discover other resouces along the way that allow you to learn more.
For example, if you were curious and wanted to learn more about the commands used above you can do.

```

man chmod

```

or 

```

man sudo

```

and you'll get information on how they are used and what they do (The 'q' key quits the man page).
Anyway, try to fix your current issue then you can explore.

---

### Post by crowdedelevator on 2010-01-06
I would love to. But now grub isn't loading, so im doing a fresh reinstall of karmic.  Someone in my house I trying to upset me. I went to bed with karmic koala live cd in my disc tray, and I woke up with jaunty jackolope in in and karmic on the floor.... so I think someone tried to play a joke and actually caused trouble.  Its my fault for leaving things out.  And I can't get the forum tools to work on my cell  Its one problem after another. The best way to learn I guess

---

