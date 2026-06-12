---
title: "Samba and mounting"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by carusoswi on 2007-04-15
How does one mount the drives that are visible on the network from within Samba.  I tried my hand at mounting manually, and received this message:

smbmnt must be installed suid root for direct user mounts (1000,1000)

What does that message mean and how shall I respond?

Thanks.

Caruso

---

### Post by TheWizzard on 2007-04-15
use this command: 

```
sudo mount -t cifs -o credentials=/home/XXX/.smbpasswd,noperm //athlon/home /mnt/athlon
```


in /etc/sudoers set:
XXX ALL=NOPASSWD: /bin/mount,/bin/umount

the file /home/XXX/.smbpasswd contains your samba username + password


XXX is your username

---

### Post by carusoswi on 2007-04-15
Sorry, how do I go about setting that soders deal that you mentioned towards the end of your post.  Doesn't seem to work from the terminal, and I cannot open sodoers with my text editor.

Ran everything up until then, only my computer is visible to samba at the moment.  Don't know if that's because I didn't finish everything you told me to do, or because it didn't work for me.

Additional help welcome, and thanks for the suggestions.  I probably am missing something.

Caruso

---

### Post by carusoswi on 2007-04-15
Well, I lost the ability to see other machines on my network earlier this afternoon, but was able to sudo dpkg --purge --force-remove-reinstreq smb4k to remove Samba, then, reinstall it and the resources on the network were again visible.

After running the commands above, I have been unable to get those resources to show up again (printers, computers, etc.).

Still don't know why - certainly not sore about it - this is, afterall, Ubuntu.  In the few short weeks I've been messing around with it (weekends only), I have come to count on the ability to recover from just about anything I might do to my machine from someone on this forum who will help me find a way out.

Ok, then, folks, don't fail me now!!

What did I do wrong - what did I do right to get that stuff to reappear, what should I do right again, and, after they show up again, how do I go about mounting them.

Samba has a dialog box where one might mount these resources "manually", I just don't know what to enter there.  I assume that, until I sort out the problems that is making those resources not to appear, nothing I do in that dialog box will be of any value.

Advice most appreciated.

Caruso

---

### Post by carusoswi on 2007-04-15
Well, Samba has a search function, so I entered the IP address of one of the other computers (I knew I could ping that machine from the System-Networking menu).  Samba found it, I clicked the checkmark, and everything is showing up again.

Now, if only I know how to type in what is necessary to instruct Samba to mount those devices.

Anyone?

Caruso

---

### Post by carusoswi on 2007-04-15
The name of the other computer is ROCK.
I can see a tree that contains C, ICP$, Owner, Print$, Printer, Sharedocs.

In the "mount manually" Samba dialog box, I entered //Rock/Share, then, in the space for the address, I entered the IP address, and below that, the workgroup name.

Pressing OK invokes the glass shattering error notification.  Details button reveals this message:

6698: tree connect failed: ERRDOS - ERRnosuchshare (you specified an invalid share name)
SMB connection failed

----so, can someone tell me what I am doing wrong.

it feels as though I'm getting close to something - but death will come to me sometime in the next 100 years or so, and I aim to have figured this little puzzle out by then.

Advice would be most welcome.

Caruso

---

### Post by dmizer on 2007-04-15
try the second link in my sig.

---

### Post by carusoswi on 2007-04-20
> **TheWizzard said:**
> use this command: 

```
sudo mount -t cifs -o credentials=/home/XXX/.smbpasswd,noperm //athlon/home /mnt/athlon
```


in /etc/sudoers set:
XXX ALL=NOPASSWD: /bin/mount,/bin/umount

the file /home/XXX/.smbpasswd contains your samba username + password


XXX is your username

First command results in this error message

error 2 opening credential file /home/XXX/.smbpasswd

Caruso

---

### Post by carusoswi on 2007-04-20
> **carusoswi said:**
> First command results in this error message

error 2 opening credential file /home/XXX/.smbpasswd

Caruso

So, today, I start up Samba, scan the network, and there in the pane on the left is the tree complete with the resources on my network.

I click on the C drive for another machine, it jumps over into the right pane (apparently that means that it is mounted).

I double click it, all the icons representing folders appear.  I can double click those folders to browse the other machine at will.  Clicked on a photo file icon, and the photo appeared on my machine.

I go to open Photoshop to give it a try, and I inadvertently clicked on the icon of InDesign (which is not yet running properly on my machine).  InDesign locks up (as it does always), and I am forced to reboot.

Now, browsing my network is a thing of the past.  I'm right back to where I was last week, sometimes can see the network, sometimes can see only my machine, sometimes can not see anything.  

Does that make any sense?

Caruso

---

### Post by carusoswi on 2007-04-20
One more thing:  When my (host) machine appears in the left pane, and I click to search it, I get a message asking me to authenticate.  I type in my user name and password, but am told that access is denied.  Why?

Caruso

---

### Post by carusoswi on 2007-04-20
I think there is something wrong with this program.  Just now, the network directory tree re-appeared.  I can select a remote drive, click on share, the icon for the drive flashes in the right pane and the message in the status line at the lower portion of the left pane says "DONE", but the icon only shows up briefly, then disappears.

I believe something isn't right, here.  Also, the program does not react consistently.  That coupled with my inexperience with this program - not knowing exactly what it is supposed to do - is complicating my troubleshooting efforts.

But, I am guessing that this may not be a setup/installation problem or I would not have experienced a momentary moment of total success.

Any advice out there (sorry to keep posting back in this thread, almost talking to myself, but, if I don't post my progression, no one will be able to offer advice.

Thanks to anyone who can help.

Caruso

---

### Post by TheWizzard on 2007-04-20
> **carusoswi said:**
> First command results in this error message

error 2 opening credential file /home/XXX/.smbpasswd


you have to make the file with credentials of course.

---

### Post by carusoswi on 2007-04-21
> **TheWizzard said:**
> you have to make the file with credentials of course.

Could you clarify, please?

What does that mean, make the file with credentials.  How do I do that?

I am the only one using my machine, so, I don't understand what credentials I need.

Also, I only use one password on this machine, ever.  So, I don't know why I keep getting an error message when Samba asks me for my password.  I have checked and double checked.  Spelling and case are correct for all characters.

Thanks for the reply - but I do need additional clarification.


Caruso

---

### Post by TheWizzard on 2007-04-22
> **carusoswi said:**
> Could you clarify, please?

What does that mean, make the file with credentials.  How do I do that?


you don't have to put ypour username & password in a file. you can also use this command:

```
sudo mount -t cifs -o user=you,passwrd=xxx,noperm //athlon/home /mnt/athlon
```



> **carusoswi said:**
> Also, I only use one password on this machine, ever.  So, I don't know why I keep getting an error message when Samba asks me for my password.  I have checked and double checked.  Spelling and case are correct for all characters.

Thanks for the reply - but I do need additional clarification.


Caruso

please be clear with your questions and descriptions of your problem. you are quit vague. when does samba ask you for a password? 
please provide the exact commands you type and exactly what the computer returns.

---

### Post by Detonate on 2007-04-22
In smb4k under Settings>Configure Smb4k click on Superuser and check the box by "Use super user privileges to mount and umount'.  While you are in there, you can also change the default mount directory.  You should then be able to mount the visible folders.

---

### Post by total wormage on 2007-04-23
i don't understand why no-one told the threadstarted to just use:
```
sudo chmod +s /usr/bin/smbmnt
```

---

### Post by carusoswi on 2007-04-24
Thanks to all for the replies.  I am away from my network (and from the 'net via Ubuntu) until this weekend.  For now, it's one machine and Win'net only.  But, I have read your responses and remain anxious to try out your suggestions.

Sorry if some of my questions were vague.  In many of my posts, I am just "thinking  out loud."

Samba asks me for a password whenever I click in the left pane to mount the main drive of my host machine.  I am asked to enter my user ID and password.  Sorry, I cannot be more precise than that from memory.

Anyhow, when I enter ID/password, the screen to enter same keeps popping back up because those credentials are not recognized as valid.

Secure or not, to avoid these types of situations, I practice using one set of credentials universally, so, I know that Samba cannot have any other password/ID other than what I am offering it.

Again, thanks for your input.

Caruso

---

### Post by TheWizzard on 2007-04-24
> **carusoswi said:**
> Thanks to all for the replies.  I am away from my network (and from the 'net via Ubuntu) until this weekend.  For now, it's one machine and Win'net only.  But, I have read your responses and remain anxious to try out your suggestions.

Sorry if some of my questions were vague.  In many of my posts, I am just "thinking  out loud."

Samba asks me for a password whenever I click in the left pane to mount the main drive of my host machine.  I am asked to enter my user ID and password.  Sorry, I cannot be more precise than that from memory.



ok, you're trying to mount using a gui. i'm afraid i can't help you with this because i always use the command line to mount. 
it's worth a try to mount from the command line. the command line gives clear error messages and makes it possible to make a script to mount on startup.

---

### Post by carusoswi on 2007-04-25
> **TheWizzard said:**
> ok, you're trying to mount using a gui. i'm afraid i can't help you with this because i always use the command line to mount. 
it's worth a try to mount from the command line. the command line gives clear error messages and makes it possible to make a script to mount on startup.

What is the command to mount a network drive from the command line?

Caruso

---

### Post by TheWizzard on 2007-04-26
> **carusoswi said:**
> What is the command to mount a network drive from the command line?

Caruso

```
sudo mount -t cifs -o user=you,passwrd=xxx,noperm //athlon/home /mnt/athlon
```

---

### Post by s13_mills on 2007-05-01
Hi there,

I had the same problem with smb4k. This method was mentioned earlier, but I had to do a little more to make it work 100%. Solved with the following:

```
sudo chmod u+s /usr/bin/smbmnt
sudo chmod u+s /usr/bin/smbumount
```

Now smb4k works fine, I quite like it as a utility, made accessing the shares in my flat much easier as I can just mount them wherever, then get at them quickly!

---

