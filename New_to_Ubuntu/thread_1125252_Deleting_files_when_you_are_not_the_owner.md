---
title: "Deleting files when you are not the owner"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by mameshiba on 2009-04-14
Hello,

I'm new to the forums and this is my first post. I really like using Ubuntu, which I use at home. I think I'm running Intrepid Ibex but I'm not completely sure :confused:

The reason I need help today is because I used to share my PC with someone who I was living with at the time. They left a load of files on my hard drive, which are surplus to requirements now and which I would like to delete (MP3s mostly) to save disk space. However, as I am not the owner of these files I do not have permission to do this. The other user no longer has a user account on the PC - they deleted their account when they gave me my PC back.

I've googled and I've looked through the FAQs on the main UBUNTU website, but I haven't been able to find any instructions on how I can override this - does anyone have any ideas?

Thanks very much in anticipation!):P

---

### Post by _Purple_ on 2009-04-14
Are you the root user? I mean do you know the password for sudo?

---

### Post by mcduck on 2009-04-14
Assuming you are the one with admin account on the machine, just hit alt-F2 and run "gksudo nautilus" to start the file amanger with root permissions. You can then use that to delete the files you need to remove.

As a tip, anything deleted this way will end in root's trash bin instead of your normal user's. To avoid having to go to empty root's trash afterwards you can use shift+delete to remove the files immediately instead of moving them to trash.

Of course you should be careful with this, as Nautilus running as root allows you to mess with any files & directories, including important system stuff, and shift+delete is quite final way to delete files, should you accidentally remove wrong file it would be pretty hard (if not impossible) to recover it again.

---

### Post by steve101101 on 2009-04-14
When I was first using Linux, I accidentally deleted systems files doing this so be very careful when using any command with sudo  or root powers.

---

### Post by s.fox on 2009-04-14
Hi,

This may be the long way around the problem but you could do something like this:

```
sudo chmod 666 file.mp3
```You will be prompted for sudo password.  After you have entered the password and pressed enter you should be able to delete the file like normal.   

-Ash R

---

### Post by Jakey_TheSnake on 2009-04-14
^ For that, *.mp3 would be better. Or just * for everything inside the directory. Meh.


What is the filepath of the other users documents? If the folder is, say "barbara" inside the home folder, then:

```
sudo rm -rf /home/barbara
```

would do it. 

But personally, I'd just enter "gksudo nautilus" and delete from there.

---

### Post by steve101101 on 2009-04-14
> **Jakey_TheSnake said:**
> ^ For that, *.mp3 would be better. Or just * for everything inside the directory. Meh.


What is the filepath of the other users documents? If the folder is, say "barbara" inside the home folder, then:

```
sudo rm -rf /home/barbara
```

would do it. 

But personally, I'd just enter "gksudo nautilus" and delete from there.

graphic interfaces are usually easier to make sure you realize what you are doing.

---

### Post by nothingspecial on 2009-04-14
> **Jakey_TheSnake said:**
> 

```
sudo rm -rf /home/barbara
```



[SIZE="3"][COLOR="Red"]Do not type this wrong! If you leave a space inbetween "/" and "home" you might annihilate your entire system!![/COLOR][/SIZE]

---

### Post by Jakey_TheSnake on 2009-04-14
> **steve101101 said:**
> graphic interfaces are usually easier to make sure you realize what you are doing.

That is precisely why I said I'd use gksudo nautilus >_>

---

### Post by nothingspecial on 2009-04-14
Sorry. you weren`t talking to me

---

### Post by Jakey_TheSnake on 2009-04-14
Uhhmmm? No I wasn't :) 

On a side note, why is there no simple "del" command in the terminal, like DOS has?

---

### Post by mcduck on 2009-04-15
> **Jakey_TheSnake said:**
> Uhhmmm? No I wasn't :) 

On a side note, why is there no simple "del" command in the terminal, like DOS has?

Yes, there is. "rm". And it's even simpler than in DOS, 2 letters when compared to 3. :D

---

