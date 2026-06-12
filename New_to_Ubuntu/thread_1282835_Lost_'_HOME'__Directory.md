---
title: "Lost ' /HOME'  Directory"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by barnaclebill18 on 2009-10-04
Hello,

My first attempt to really do something using the terminal on Ubuntu Jaunty did not work out well.

I thought I would move HOME to a separate partition, and used this guide [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome).

Well I must have done something wrong, now I can't boot up Ubuntu.

When I turn on the computer, after it starts loading a message comes up: Your HOME directory is listed as :'/home/bill/bill' but it does not appear to exist. Do you want to log in with the /(root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session. YES or NO

If I say yes or no it does the same thing, a log in screen comes on and when I try to log in another box comes up: User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by a user and have 644 permissions. User's #HOME directory must be owned by a user and not writable by others.

Then it just sits there with a black screen.

Help.  Thanks

---

### Post by crispy_420 on 2009-10-04
Just going to throw this idea out there. Please point me out if I am wrong but couldn't you boot to rescue option instead of standard by hitting escape when it asks during boot. From there shouldn't you be able to create a new user and associated password.

Just throwing out that idea.

From the new account you could then search for those misplaced files and move them into new account. Also may want to change the permissions to those of the new account.

---

### Post by drs305 on 2009-10-04
I wrote a guide on recovering from a .dmrc error but in this case the problem isn't a permission one but of the system not finding /home.

Have you placed an entry for /home in your fstab file? Does it contain the correct UUID?

If you tell us what partition now contains your /home, and post the results of the following perhaps we can help:
```

sudo blkid -c /dev/null  # provide refreshed UUID information
cat /etc/fstab  # display the contents of fstab

```

If you are running the liveCD, you would have to mount your system partition to a folder first, then include the complete path in the "cat" command above. For instance, if your real / was on sda1, mount sda1 to /mnt/temp, then "cat /mnt/temp/etc/fstab". If you need more complete instructions as to what I mean let us know.

---

### Post by barnaclebill18 on 2009-10-04
I don't know what I did other than try to follow the guide.

How can I run the commands suggested if I can't get Ubuntu to boot?

I tried the recovery boot option, but could not figure it out.

I am a computer dummy and need explicit, step by step instructions.

---

### Post by crispy_420 on 2009-10-04
It flashes really quickly at boot but there is a reference to "ESC" to choose boot options or something of that nature. Then there should be a list of kernels available and a matching "(recovery mode)" under each kernel. You can than highlight your recovery choice and hopefully boot from it.

That any help?

---

### Post by blackmail on 2009-10-04
A straigh forward solution would be to boot your liveCD, and start partition editor (I am not sure it is called like that, any way you can find it at System->Administration->partition...)
There you will find your home listed. all you have to do is edit the /etc/fstab file on your root partition, and insert the appropriate information. [This]("http://help.adobe.com/en_US/Acrobat/9.0/Standard/WSB596A120-CCC1-4adc-BDFE-277E588CCEF3.html") thread should help you understand the fstab file.
If all you are missing is your /home directory then you are ok if you do this.
If you get bored with this and decide to reinstall ubuntu, mark your home partition as home and unmark the format option. But that option you shouldn't consider since it is not such a big problem.

---

### Post by gali98 on 2009-10-04
It sounds like your fstab may be set up wrong...
My guess is that your entry has "/home/bill" when it should just be "/home"...
You might boot into recovery mode and use nano (text editor) to fix the entry and try rebooting...
Kory

Edit: or if that doesn't work, upload your fstab and let us check it out - /etc/fstab

---

### Post by barnaclebill18 on 2009-10-04
Thanks for all the replys.

I tried recovery again, I now have a screen that says: Recovery Menu, and lists Resume normal boot, clean Try to make free space, dpkp Repair broken packages, fsck File system check, grub Update grub bootloader, netroot Drop to root shell prompt with networking.

I do not know how to procede.

---

### Post by gali98 on 2009-10-04
Do the drop to root shell.
That will give you a terminal. You may have to put in your password.
Then run:
nano /etc/fstab 
and give us the contents (if you don't understand my instructions from the post above.)
Kory

---

### Post by barnaclebill18 on 2009-10-05
The up and down arrow keys move the highlight, but how do I choose OK or cancel, the two choices?

I moved the highlight to Drop to root shell, I hit enter and a thing came up at the bottom of the screen: root@bill-laptop:~#

But I do not know what to do next, remember I am really new to this stuff.

---

### Post by crispy_420 on 2009-10-05
[Create new user]("http://www.cyberciti.biz/faq/howto-add-new-linux-user-account/")

[Another source]("http://www.ahinc.com/linux101/users.htm")

---

### Post by barnaclebill18 on 2009-10-05
I do not know if I need to create a new user account, any way it is getting real late here and I am falling asleep, I will continue with this in the morning.

Thanks everyone.

---

### Post by barnaclebill18 on 2009-10-05
> **gali98 said:**
> Do the drop to root shell.
That will give you a terminal. You may have to put in your password.
Then run:
nano /etc/fstab 
and give us the contents (if you don't understand my instructions from the post above.)
Kory

I ran nano /etc/fstab, but it is a full screen and I do not know how I can copy and paste anything without the mouse and I am writing this on another computer.

13 lines came up:

# /etc/fstab: static file system information.
#
Use 'vol_id --uuid' to print the universally unique identifer for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if discs are added and removed. See fstab(5).
#
# <file system> <mount point>  <type>  <options> <dump> <pass>
proc             /proc          proc    defaults   0      0
# / was on /dev.sda5 during installation
UUID=b6355534c-7c6b-462c-a2e4-a8e14c74b5c5 /   ext3  relatime,erro$
# swap was on /dev/sda6 during installation
#UUID=9f9fa3b0-b478-4ac7-bcae-9e3074d0f397 none  swap  sw  $/dev/scd0  /media/cdrom0  udf,iso9660 user, noauto,exec,utf8 0

I have no idea what this means or what to do next.

---

### Post by drs305 on 2009-10-05
> **barnaclebill18 said:**
> 
# /etc/fstab: static file system information.
#
Use 'vol_id --uuid' to print the universally unique identifer for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if discs are added and removed. See fstab(5).
#
# <file system> <mount point>  <type>  <options> <dump> <pass>
proc             /proc          proc    defaults   0      0
# / was on /dev.sda5 during installation
UUID=b6355534c-7c6b-462c-a2e4-a8e14c74b5c5 /   ext3  relatime,erro$
# swap was on /dev/sda6 during installation
**#UUID=9f9fa3b0-b478-4ac7-bcae-9e3074d0f397 none  swap  sw  $/dev/scd0  /media/cdrom0  udf,iso9660 user, noauto,exec,utf8 0**

I have no idea what this means or what to do next.

OK, we can guide you through this. Your fstab just needs a few additions.

First, lets clean up what is there.
Make the line in bold look like this (make two lines, and add a 0  at the end):
[B]#UUID=9f9fa3b0-b478-4ac7-bcae-9e3074d0f397 none  swap  sw 
$/dev/scd0  /media/cdrom0  udf,iso9660 user, noauto,exec,utf8  0 0[/B]

Now the important one. You don't have a /home partition listed. Add this line:
> 
/dev/**sda3** /home ext3 nodev,nosuid 0 2

Change **sda3** to the partition your /home is now on. If you don't know, tell us.

Save the file. In nano, save the file by hitting CTRL-X, Y then ENTER. Hopefully this will allow your system to boot into a normal system. 

We will still need to tweak your fstab once you get a working system.

Reboot.

---

### Post by barnaclebill18 on 2009-10-05
I am pretty sure the HOME file is still on the original partition, I looked at the disc with a Gparted live CD and the new partition I made had nothing on it.

Somehow I think the name just got changed.

Thanks

---

### Post by drs305 on 2009-10-05
I'm not clear on how you are booting at the moment. If you can boot to the recovery mode root shell prompt, do that and create a new user, bill1, and then give him admin rights. Once you can boot as a normal user we can sort out what you have on your system and get you back to your original user and configuration files.
Since you will be in a root shell, you won't need to use "sudo".
```

adduser bill1  # enter a password when asked (suggest using same as old one)
adduser bill1 admin  # Give new user admin (sudo) privileges

```
Reboot and log in as bill1.

---

### Post by barnaclebill18 on 2009-10-05
First, lets clean up what is there.
Make the line in bold look like this (make two lines, and add a 0 at the end):
#UUID=9f9fa3b0-b478-4ac7-bcae-9e3074d0f397 none swap sw
$/dev/scd0 /media/cdrom0 udf,iso9660 user, noauto,exec,utf8 0 0

I had left the last 0 off when I typed the reply, that line looks OK


Now the important one. You don't have a /home partition listed. Add this line:
Quote:
/dev/sda3 /home ext3 nodev,nosuid 0 2
Change sda3 to the partition your /home is now on. If you don't know, tell us.

Save the file. In nano, save the file by hitting CTRL-X, Y then ENTER. Hopefully this will allow your system to boot into a normal system.

We will still need to tweak your fstab once you get a working system.

I did this but it asked me for Y or NO, I typed y and it does not look like anything changed on the screen except for the new line.

---

### Post by barnaclebill18 on 2009-10-05
I'm not clear on how you are booting at the moment. If you can boot to the recovery mode root shell prompt, do that and create a new user, bill1, and then give him admin rights. Once you can boot as a normal user we can sort out what you have on your system and get you back to your original user and configuration files.
Since you will be in a root shell, you won't need to use "sudo".
Code:

adduser bill1  # enter a password when asked (suggest using same as old one)
adduser bill1 admin  # Give new user admin (sudo) privileges

Reboot and log in as bill1.

I did this and at the end it asked if all the information was correct and I answered Y and it said bash: Y: command not found.

---

### Post by renkinjutsu on 2009-10-05
he doesn't have a home partition in his fstab because he never had a home partition to begin with.. his /home is probably still on / /dev/sda5

reading his initial post, he says the error tells him that his home is listed as /home/bill/bill .. let's fix that problem first.

i think his fstab looks all messed up because he tried to copy it straight out of nano.

----

When you're in recovery mode, do ```
ls /home/bill
```
to see if the contents of your home directory is still on /dev/sda1 .. if it's still there, then continue

then, to fix the initial problem "home resolving to /home/bill/bill" do this ```
usermod -d /home/bill bill
```
this should change your home back to /home/bill

now you can reboot and try to login as bill
then report back to the forums!

---

### Post by barnaclebill18 on 2009-10-05
When you're in recovery mode, do
Code:

ls /home/bill

When I do this it says 1s /home/bill

command not found

---

### Post by drs305 on 2009-10-05
> **barnaclebill18 said:**
> When you're in recovery mode, do
Code:

ls /home/bill

When I do this it says 1s /home/bill

command not found

It looks like you typed a one ( 1 ) instead of a lowercase L.

---

### Post by barnaclebill18 on 2009-10-05
It looks like you typed a one ( 1 ) instead of a lowercase L.

I used a 1

When I copied and pasted the reply it just looked like an l

---

### Post by drs305 on 2009-10-05
> **barnaclebill18 said:**
> It looks like you typed a one ( 1 ) instead of a lowercase L.

I used a 1

When I copied and pasted the reply it just looked like an l

? 
It *should* be a lowercase L. Did it show contents for /home/bill ?

---

### Post by barnaclebill18 on 2009-10-05
I just tried making another new user because I might have already had a bill1 user account.

Anyway after it asked for a password and it said password updated successfully, it said enter a new value, or press ENTER for the default and I accidentally hit a key but the backspace key will not remove what I typed.

---

### Post by renkinjutsu on 2009-10-05
it's horrible when that happens..

means you'll have to start over.. Press ctrl and C to exit it


also.. why did you decide to continue with bill1? You already had admin access in the recovery console :confused:

---

### Post by drs305 on 2009-10-05
> **barnaclebill18 said:**
> I just tried making another new user because I might have already had a bill1 user account.

Anyway after it asked for a password and it said password updated successfully, it said enter a new value, or press ENTER for the default and I accidentally hit a key but the backspace key will not remove what I typed.

You can actually *see* what you typed? Generally in terminal you won't see passwords as you type but you can use backspace many times to get back to the start and retype it.

In this case, if you can't back out of what you typed, I guess you can either remember what you enter or create *another* user with a correct password. You will be able to delete any users you create later as long as the new user has admin rights.

---

### Post by barnaclebill18 on 2009-10-05
You can actually see what you typed? Generally in terminal you won't see passwords as you type but you can use backspace many times to get back to the start and retype it.

In this case, if you can't back out of what you typed, I guess you can either remember what you enter or create another user with a correct password. You will be able to delete any users you create later as long as the new user has admin rights.

I could not see the password, after it said successful is when I made the error.

I guess I will have to start over and try again, this CLI stuff is really hard on  an old guy that is dumb.

---

### Post by drs305 on 2009-10-05
> **barnaclebill18 said:**
> You can actually see what you typed? Generally in terminal you won't see passwords as you type but you can use backspace many times to get back to the start and retype it.

In this case, if you can't back out of what you typed, I guess you can either remember what you enter or create another user with a correct password. You will be able to delete any users you create later as long as the new user has admin rights.

I could not see the password, after it said successful is when I made the error.

I guess I will have to start over and try again, this CLI stuff is really hard on  an old guy that is dumb.

Hey, it's a learning experience. By the way, it makes it easier to follow the thread if, should you need to quote the previous post, you use the "quote" feature. You can either hit the "Quote" button at the lower right of the post to initiate a new post quoting the previous one, or if you are already composing and want to include a quote, hit the # symbol in the menu at the top of the post. This will generate a [noparse]> [/noparse] entry. Paste the stuff you want to quote within.

---

### Post by renkinjutsu on 2009-10-05
don't be hard on yourself.. many of us have been around here for a loong time

and you only get smarter when you hang around the ubuntuforums ;) because there are always people so much smarter than yourself and if you give up and leave, you'll miss out on some serious learn'in.


so did you ever try doing `ls /home/bill` again?

---

### Post by barnaclebill18 on 2009-10-05
Something is not working right when I use the quote button, the quote is there but I can not type in the box, that is why I was doing it that way.

When I hit the # above this right now it just makes the cursor disappear.

---

### Post by drs305 on 2009-10-05
No problem. Just wanted to make sure you knew it was available.

Did you ever try what renkinjutsu recommended in post 19? 

Or give us an update on where you are in the process. If you created a new user and were able to log on, we can try to clean things up and restore your original.

---

### Post by barnaclebill18 on 2009-10-05
> **renkinjutsu said:**
> don't be hard on yourself.. many of us have been around here for a loong time

and you only get smarter when you hang around the ubuntuforums ;) because there are always people so much smarter than yourself and if you give up and leave, you'll miss out on some serious learn'in.


so did you ever try doing `ls /home/bill` again?

It worked this time.

I just tried ls '/ home/bill' again and it said No such file or directory.

---

### Post by barnaclebill18 on 2009-10-05
> **drs305 said:**
> No problem. Just wanted to make sure you knew it was available.

Did you ever try what renkinjutsu recommended in post 19? 

Or give us an update on where you are in the process. If you created a new user and were able to log on, we can try to clean things up and restore your original.

I have not tried rebooting because I don't think I made any successful changes, but I could try that I guess.

I still don't know if it should be a 1 or l

From post 19 I thought it was a 1

---

### Post by barnaclebill18 on 2009-10-05
I just tried rebooting and used the older kernel option and it is still the same way and wont load the OS.

---

### Post by drs305 on 2009-10-05
> **barnaclebill18 said:**
> I have not tried rebooting because I don't think I made any successful changes, but I could try that I guess.

I still don't know if it should be a 1 or l

From post 19 I thought it was a 1

No, it's a lowercase L. The command is to List things:
```

ls /home/bill

```

If you have already created a new user and know the password, it would probably be worthwhile at this point to go ahead and try to log in with the new one.

I sent you a PM as well.

---

### Post by gali98 on 2009-10-05
How about this.
Type:
```
ls /home
```
Kory

---

### Post by barnaclebill18 on 2009-10-05
> **gali98 said:**
> How about this.
Type:
```
ls /home
```
Kory

Now when I tried that 3 entries came up:

bill1

bill3

bill4

I guess the are what I made earlier today.

---

### Post by renkinjutsu on 2009-10-05
wow.. that's everything but your original username
is your username already on the new partition then?

check with this

```
sudo mount /dev/sda7 /mnt
ls /mnt/home
```

If you're in the root recovery console, you won't need sudo
i think it's /dev/sda7
do ```
fdisk -l
```
to make sure it's the last partition on the list
and it's a lower case L :wink:


edit: thanks drs305

---

### Post by barnaclebill18 on 2009-10-05
> **renkinjutsu said:**
> wow.. that's everything but your original username
is your username already on the new partition then?

check with this

```
sudo mount /dev/sda3 /mnt
ls /mnt/home
```

If you're in the root recovery console, you won't need sudo

edit: thanks drs305

I guess I better come clean with you guys, after this happened I used that partition to put Mint on, and when in Mint I can access my old home folder in Ubuntu and copy and pasted all my stuff into Mint. That is how I know the home is still on the Ubuntu partition.

I am really trying to learn something about Linux and that is why I am trying to fix this without reinstalling.

---

### Post by drs305 on 2009-10-05
Having other distributions is no crime. Heck, all of us except for the youngest, once used some other OS. It just would have made troubleshooting this a lot easier...

Anyway, so are you saying your original /home/bill still exists (somewhere) on sda1, which is your Ubuntu install?

When you ran "ls /home" it didn't come up with "bill", just bill1,2,3... Where are you copying your existing "bill" home from to put into Mint? Or did you accidentally *move* it into Mint instead of copy it?

[http://paste.ubuntu.com/286673/]("http://paste.ubuntu.com/286673/")

---

### Post by barnaclebill18 on 2009-10-05
> **drs305 said:**
> Having other distributions is no crime. Heck, all of us except for the youngest, once used some other OS. It just would have made troubleshooting this a lot easier...

Anyway, so are you saying your original /home/bill still exists (somewhere) on sda1, which is your Ubuntu install?

When you ran "ls /home" it didn't come up with "bill", just bill1,2,3... Where are you copying your existing "bill" home from to put into Mint? Or did you accidentally *move* it into Mint instead of copy it?

Ubuntu is on sda5, Mint is on sda3 and they share sda6, i think for swap.

I did not move them, just copied and put them in Mint home.

I have to leave right now for a couple hours, I will continue this later this afternoon.

Thank you for the help, sorry if I misled you.

---

### Post by renkinjutsu on 2009-10-05
His ubuntu install is on /dev/sda5 .. i think he made it a logical partition.. (love logical partitions)
edit: oops.. did not see there was a 2nd page


anyway.. it IS possible for 2 distros to share the same /home partition.. you can have both Mint AND Ubuntu use the /home/bill if you put it on the newly made partition like you intended to..

---

### Post by barnaclebill18 on 2009-10-06
Ubuntu is working good again, thanks to this forum and especially drs305, Dave helped me by going way above what I would expect from a stranger that took pity on a guy that did not know what he was doing.

Anyway we were able to access the missing files through Mint and all is good now.

Thanks everyone.

---

### Post by gali98 on 2009-10-06
That's what we're here for :) We all had to learn some way...
Kory

---

