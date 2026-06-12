---
title: "fstab edit and saving problem"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by MentalOxide on 2009-02-14
Situation:

Tried a new way of mounting my iriver e100 (yes, 9 months on and I still can't get linux to mount my e100.). Found this advice [http://tuxtraining.com/2008/12/26/how-to-get-your-iriver-e100-working-nicely-in-linux](http://tuxtraining.com/2008/12/26/how-to-get-your-iriver-e100-working-nicely-in-linux)

Followed instuctions on how to edit fstab, (# sudo vim /etc/fstab
) but closed the terminal window while editing, to find out if my e100 was on sda or sdb. Came back to the terminal and typed (# sudo vim /etc/fstab
) and received a message telling me that the another copy of fstab was being used and asked me if i wanted to recover the orignal or use the .fstab.swp file. I chose to recover the original incase I stuffed up something. then was told to delete the swp version of the file, soI did. 
Then attempted to edit the fstab file which was successful, but i couldn't figure out how to save the changes i made in the terminal, so i jst closed it hoping that would just save it. But upon attempting to mount the e100 i was told that fstab didn't contain the directory for it. So I tried to edit fstab again and was told, again, that another version of the file existed, just like last time. This time I chose to recover the swp file, and was again received the message to delete the .fstab.swp file. Now i started to get worried, wondering that i might be deleting the file i just asked to use. So i panicked and closed the terminal again and can now see in the /etc directory that I have .fstab.swp , and in addition .fstab.swo , and .fstab.swn. What have I done? should i try to delete them or what?

So all of this happened because I didn't know how to save file edit changes in the terminal. So could someone please tell me how that is done? 
And how close am I to screwing up my computer messing with fstab like that?


tried to

---

### Post by kk0sse54 on 2009-02-14
No you are not screwing up your computer, vim makes a swap file to make sure no two people are editing the same file at once. Recover and delete the swp and then go back and edit your fstab with vim. In order to save the changes you need to press :w or to save and quite :wq. Vim commands can be confusing at first so I suggest looking up the basic ones first.

---

### Post by Paqman on 2009-02-14
Yeuch, vim! Who told you to use that? It's definitely not newbie-friendly. It's a specialist text-editor for people that do heavy-duty work on plain text files (ie: programmers)

For a slightly more usable text editor, try nano:
```
sudo nano /etc/fstab
```
It has it's keyboard shortcuts at the bottom of the window.

---

### Post by niteshifter on 2009-02-14
> **Paqman said:**
> Yeuch, vim! Who told you to use that? It's definitely not newbie-friendly. It's a specialist text-editor for people that do heavy-duty work on plain text files (ie: programmers)

For a slightly more usable text editor, try nano:
```
sudo nano /etc/fstab
```
It has it's keyboard shortcuts at the bottom of the window.

+1 on vi and it's demonic progeny (emacs guy here) ;)

This might be easier for the OP:
For the "privileged" stuff, that is owned by root like fstab:
```
gksu gedit /etc/fstab &
```

The terminal window will still be active, you can give other commands if need be - or even close it - and Gedit with the file will still be there.

---

### Post by Paqman on 2009-02-15
> **niteshifter said:**
> +1 on vi and it's demonic progeny (emacs guy here) ;)

This might be easier for the OP:
For the "privileged" stuff, that is owned by root like fstab:
```
gksu gedit /etc/fstab &
```

The terminal window will still be active, you can give other commands if need be - or even close it - and Gedit with the file will still be there.

If you edit fstab with Gedit, it will complain about the formatting ("No final newline", IIRC) Not a biggy, but if you use a terminal text editor it will get it right.

---

### Post by niteshifter on 2009-02-15
Hi,

> If you edit fstab with Gedit, it will complain about the formatting ("No final newline", IIRC) Not a biggy, but if you use a terminal text editor it will get it right.

Now that you mention it ... I believe I've seen that behavior some time back (early Fedora maybe?). I tried it before I posted it - no complaints  - but I've had at my fstab with xemacs.

I just now tried it on a fresh VM install of Ibex, no complaints in either terminal window or from Gedit itself, loaded right up ready for edits.

---

