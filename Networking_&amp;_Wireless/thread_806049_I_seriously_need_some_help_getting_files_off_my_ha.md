---
title: "I seriously need some help getting files off my hard drive over the network..."
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by Intelligitimate on 2008-05-24
Ok, I am in a real bind. For the background story, go to this thread:

[http://ubuntuforums.org/showthread.php?t=805462](http://ubuntuforums.org/showthread.php?t=805462)

Now, what I need to do, is find anyway possible to get the data off my hard drive that I want to keep. This is basically just some personal files and my emails, everything else can go back to the manufacturer for wiping. I have tried physically removing the hard drive, but every other computer I have doesn't have the plugs required. The computer boots up, and I can listen for the sound of the login screen, and then type my username and password, and hear the sound it makes when loading the desktop. However, all my attempts to connect to the computer over the network are refused, save what I have done via Samba, which is just a single folder with some unimportant files in it. Winscp and SSH both get “connection refused”. It gets on the network and is assigned an IP address, it just won't let any other computer connect to it, save for that single sharing folder I set up.

So my question is, how do I –blindly-- allow a network connection to go through that will let me transfer the files I want to keep somewhere else (preferably with Winscp)? I know I hit ctrl-alt-enter to open up a terminal window and start typing. But everything I've tried has failed so far.

Can anyone please help me get connected to this machine? Also, pretty much the only files I would want to keep are in folders whose locations I have memorized, save the Evolution emails.

---

### Post by jetsam on 2008-05-24
There's another thread here with another user successfully navigating this problem: 
[[SOLVED] Need to access files on computer blindly! Important!]("http://ubuntuforums.org/showthread.php?t=741391")

His solution there was pretty difficult, though; he created his own customized boot disk.  I think you should try the blind install of openssh-server first.  Boot up the computer and log in, then:

[LIST=1]
[*]Hit **ctrl**-**alt**-**f1**.
[*]Enter your username and <hit enter>.
[*]Enter your password and <hit enter>.
[*]You could use this command to verify you logged in successfully. It will say "hello" if you're at a command prompt: **espeak hello** <hit enter>
[*]Type **sudo apt-get install openssh-server** and <hit enter>.
[*]Enter your password and <hit enter>. (Authenticates sudo from above command.)
[*]Type **Y** and <hit enter>.  (This says yes to "Do you want to continue [Y/n]" from apt-get.)
[/LIST]

Then cross your fingers and try logging in from another computer using: ```
ssh <your_username>@<your_ip_address>
```

Good luck with it...

---

### Post by Intelligitimate on 2008-05-24
Oh man, thanks a bunch jetsam. I was so glad when I heard the words "hello" and then openssh worked perfectly. I Winscp'd to the machine and nearly got everything. All I need to do now is somehow get my emails off the computer. You wouldn't by chance know where evolution stores them all, would you?

---

### Post by jetsam on 2008-05-24
Great!  Glad it's working.  :)

I don't use Evolution myself.  A forum search turned up this, linked from a thread:
[http://http://ubuntu.wordpress.com/2005/12/03/how-to-backup-evolution/]("http://http://ubuntu.wordpress.com/2005/12/03/how-to-backup-evolution/")

So I think the mails are stored in ~/.evolution, but it's important to kill evolution before you copy the directory.  I think the blog post uses tar and untar as a way of maintaining usernames and permissions on the files.

---

