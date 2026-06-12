---
title: "I lost a big project backup"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by Chris Edgell on 2009-07-02
I made the mistake of doing loads of additional work on the backup copy.  Now somehow that has gone, (I must have pressed save on the wrong version...)  Any suggestions on where I could find the backup on my xubunto operating system?  Hope I have worded all right.

---

### Post by austinpsycho on 2009-07-02
if you hit the wrong button and saved in a different format; it should be in your home directory ~/
or if your like me and save it in documents; check there; lets just hope you *did* save the changes somewhere

---

### Post by WRDN on 2009-07-02
Assuming you didn't delete it, the first place to look is in your personal home folder at /home/username.

If you know the name of the folder/file, or the extension, then you can use the find tool:

```
find /home/username -name '*.tar.gz'
```

As an example, the above command will search for all files in /home/username, that have the extension .tar.gz

---

### Post by Chris Edgell on 2009-07-02
I can click on "Home" and read through all the file folders and documents and do not see anything about anything called "Prayer".

I have to go and see how the extension looks (if I go through all the steps and close up one file without saving and see how that automatic backup file looks.

Thank both of you for your responses.  As far as going to that place with the code, would that be typed into the terminal...I'm not just new, I'm almost computer illiterate, so it requires absolute simplicity to instruct me.

---

### Post by WRDN on 2009-07-02
Yep, it needs to be entered into the Terminal found at Applications > Accessories > Terminal. If the backup is called Prayer, then replace the command in post 3 with:

```
find /home/username -name 'Prayer*'
```

Or search your entire machine for files with that name

```
find / -name 'Prayer*'
```

Note that, this will include all mounted media (e.g. external hard disk drive's).

---

### Post by tgalati4 on 2009-07-02
What was the program that you were using?  Each program has different naming conventions for its backup files.  

If you open a backup copy and work on it then close it, and then open the current copy, the backup gets immediately overwritten.  If that is what happened, then it's nearly impossible to recover the data without doing a forensic disk recover.

There are tools in linux to do that, but they can take several hours.  Probably exceeding the amount of work that you have put in already.

---

### Post by Chris Edgell on 2009-07-02
tgalati4, I was using AbiWord.  I think you described what I did. I did have a "moment of truth" in passing, telling me to get the new stuff on the original instead of using the one called backup.  Fortunately, I had finished the project (well, it was relatively big, for me, at 20 pages).  I had finished it and run a copy, but had wanted to send it to my co-worker and now must do a lot of retyping and re-grouping of info.

However, WRDN, as I tried your procedure, I discovered that I could not do it correctly enough to even find something that I knew where it was..wondering, if I show you what I typed in, can you tell me what I was doing wrong for that procedure to work in the future.  I typed:
find/ -chris June 29th. 2009.abiw(then I pressed enter)

Thanks

---

### Post by halitech on 2009-07-02
1 thing to remember when looking for files is Prayer is not the same as prayer on a unix type system.

Try opening Nautilus and press CTRL + H so it shows hidden files. I think the backup files are usually hidden and then see if you see your backup file

---

### Post by cariboo on 2009-07-02
> **Chris Edgell said:**
> tgalati4, I was using AbiWord.  I think you described what I did. I did have a "moment of truth" in passing, telling me to get the new stuff on the original instead of using the one called backup.  Fortunately, I had finished the project (well, it was relatively big, for me, at 20 pages).  I had finished it and run a copy, but had wanted to send it to my co-worker and now must do a lot of retyping and re-grouping of info.

However, WRDN, as I tried your procedure, I discovered that I could not do it correctly enough to even find something that I knew where it was..wondering, if I show you what I typed in, can you tell me what I was doing wrong for that procedure to work in the future.  I typed:
find/ -chris June 29th. 2009.abiw(then I pressed enter)

Thanks

You have to enclose your search string with qoutes eg:

```
find/ "-chris June 29th. 2009.abiw"
```

As Linux does not deal well with spaces in file names. It thinks you are looking for seperate files: -chris, June, 29th.,2009.abiw.

---

### Post by tgalati4 on 2009-07-02
As a rule, use underscores in your filenames:  Sermon_Devil_with_a_blue_dress_on_1_Jul_09.abw

Abiword does autosave every 5 minutes by default.  This can be set in Edit-->Preferences.  The default backup filename is *.bak~.

---

### Post by Chris Edgell on 2009-07-02
Hi, all...thanks for your responses!

halitech:  I think my "Thunar" is the equivalent to your "Nautilus" as I am xubuntu.  When I press Thunar I get the window that I think it's correct to call a directory named: chris-file manager.  I seem unable to find an opportunity to press CTRL+H.

cariboo907: Thanks for the tip about enclosing the search string with quotation marks. 
tgalati4:  I'll make a habit of using the underline instead of spaces.
In the meantime, I changed the name of this file to the non-space form.
And to the two of you, I was unable to get a response.  Here's what
I typed:  find/ "-chris_June_29th,_2009.abw"(enter)
Where did I go wrong...I'm going back and do it again, just to double check...

---

### Post by WRDN on 2009-07-02
You missed the space between find and /. Also, if you are unsure of the exact filename, then add "-name" to the command. Just copy and paste the command below:

```
find / -name "-chris_June_29th,_2009.abw"
```

---

### Post by Chris Edgell on 2009-07-02
I pasted that in and got a maybe a couple hundred types of "Permission denied".
I thought I had the space in there...sometimes that space looks tiny compared to THIS type-style..be that as it may...

---

### Post by Chris Edgell on 2009-07-02
chris@chris-desktop:~$ find / -name "-chris_June_29th,_2009.abw"
find: /var/lib/gdm: Permission denied
find: /var/lib/PolicyKit: Permission denied
find: /var/run/sudo: Permission denied
find: /var/run/cups/certs: Permission denied
find: /var/cache/ldconfig: Permission denied
find: /var/cache/system-tools-backends/backup: Permission denied
find: /var/spool/cron/crontabs: Permission denied
find: /var/spool/cron/atspool: Permission denied
find: /var/spool/cron/atjobs: Permission denied
find: /var/spool/cups: Permission denied
find: /tmp/gconfd-root: Permission denied
find: /tmp/orbit-root: Permission denied
find: /root/.gnome2: Permission denied
find: /root/.synaptic: Permission denied
find: /root/.gnome2_private: Permission denied
find: /root/.aptitude: Permission denied
find: /root/PDF: Permission denied
find: /root/.gconfd: Permission denied
find: /root/.gconf: Permission denied
find: /root/.hplip: Permission denied

---

### Post by halitech on 2009-07-02
> **Chris Edgell said:**
> Hi, all...thanks for your responses!

halitech:  I think my "Thunar" is the equivalent to your "Nautilus" as I am xubuntu.  When I press Thunar I get the window that I think it's correct to call a directory named: chris-file manager.  I seem unable to find an opportunity to press CTRL+H.

Your Thunar in Xubuntu is the same as my thunar in Debian. :) CRTL + H is done on the keyboard or you can go View - Show Hidden files, same result

---

### Post by Chris Edgell on 2009-07-02
I just can't seem to "get" what screen I'm to be looking at when I press CTRL+H.
It can't be just looking at the "Desktop" because nothing happens if I'm there when I press. Sorry if I sound so, how shall I say, dumb??!!

---

### Post by halitech on 2009-07-02
open Thunar and when it opens and you are looking at your files, press Crtl + H

---

### Post by Chris Edgell on 2009-07-02
I have clicked around here and there, I can't do anything with Thunar.
What can I learn about it???
  
[If I am in an open file and press Ctrl+H I do get a find and replace with box even though I'm hard pressed to find something and replace it with something else.]

---

### Post by Mornedhel on 2009-07-02
I've been following this thread without posting.

I get the feeling the OP translated the -name argument to find into -chris at some point, and is trying to find a filename with spaces in it by replacing them with underscores after another poster pointed out that spaces are usually unwieldy in the command line.

I think the correct find command is closer to this :

```
find / -name "June 29th. 2009.abw"
```

or assuming that he kept his files in his home directory,

```
find ~ -name "June 29th. 2009.abw"
```

---

### Post by Chris Edgell on 2009-07-02
Okay, (thanks for joining in); but before I go to try that, tell me, if you've read it all then you know I'm looking for the backup file--or is it most probably as one has said,really gone.  

But if I were looking for a backup file in future, would I end that line with:
2009.abw*.bak~."        ?  [do I have the *.bak~." right?]

---

### Post by Mornedhel on 2009-07-02
> **Chris Edgell said:**
> But if I were looking for a backup file in future, would I end that line with:
2009.abw*.bak~."        ?  [do I have the *.bak~." right?]

"*" means any character, or none (it's a shell glob, like in DOS, if you ever used that). It would be simpler and safer to use "*2009.abw*" to match against anything containing the string "2009.abw" anywhere in the file name. If you're looking for "any backup file", since the string "bak" is relatively uncommon except for backup files, you can use something like

```
find ~ -name "*bak*"
```

---

### Post by Chris Edgell on 2009-07-02
Oh, Mornedhel...I see some light.  Ah, yes, I "found" all the bak files--they were in the trash, but of course.  I had sent them there.  As I said earlier, I wished I had cleaned that up correctly when I found all my new work ON a backup, and continued to work there.  As someone said, next time I opened it, it reverted to the original and the bak disappeared.  Maybe, n...o that OP pretty much said it was gone.

Anyway, I then went and "found all the files that ended in 2009.abw...
Thanks for the light!!!!

---

### Post by tgalati4 on 2009-07-04
The trash can is a safety net.  You put files there and keep them a while until you empty the trash can.  Only after you empty the trash can do the files really disappear.

Keep notes of these mysterious linux commands.  You will use them again.

find ~ -name *.abw
find ~ -name *.bak

The permission denied is OK.  It means only root (administrator) can find those files.

---

