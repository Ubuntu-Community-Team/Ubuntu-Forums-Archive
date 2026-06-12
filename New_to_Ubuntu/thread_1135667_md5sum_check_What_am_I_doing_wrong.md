---
title: "md5sum check: What am I doing wrong?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by lukeinvancouver on 2009-04-24
From:
[https://help.ubuntu.com/community/HowToMD5SUM#md5sum](https://help.ubuntu.com/community/HowToMD5SUM#md5sum)


[I]"First go to the correct directory to check a downloaded iso file:
cd desktop_Ubuntu904 [ ??]
Then run the following command from within the download directory:
md5sum ubuntu-9.04-desktop-i386.iso
The md5sum should print out a single line after calculating the hash:
c564ae16dffb51a922aef74a07250473 *ubuntu-9.04-alternate-i386.iso"[/I]

(This hash is from the Ubuntuforums page.)


**This is what happened in Terminal:**

luke@ubuntu:~$ /home/luke/documents/ubuntu904
bash: /home/luke/documents/ubuntu904: No such file or directory

The directory does exist and the downloaded iso file is there.
[B]
What am I doing wrong?[/B]

:confused:

---

### Post by boof1988 on 2009-04-24
> **lukeinvancouver said:**
> From:
[https://help.ubuntu.com/community/HowToMD5SUM#md5sum](https://help.ubuntu.com/community/HowToMD5SUM#md5sum)


[I]"First go to the correct directory to check a downloaded iso file:
cd desktop_Ubuntu904 [ ??]
Then run the following command from within the download directory:
md5sum ubuntu-9.04-desktop-i386.iso
The md5sum should print out a single line after calculating the hash:
c564ae16dffb51a922aef74a07250473 *ubuntu-9.04-alternate-i386.iso"[/I]

(This hash is from the Ubuntuforums page.)


**This is what happened in Terminal:**

luke@ubuntu:~$ /home/luke/documents/ubuntu904
bash: /home/luke/documents/ubuntu904: No such file or directory

The directory does exist and the downloaded iso file is there.
[B]
What am I doing wrong?[/B]

:confused:

You need to add *cd* (for **c**hange **d**irectory) at the front of the command as shown here...

```
cd /home/luke/documents/ubuntu904
```

---

### Post by Elfy on 2009-04-24
Edit - indeed that is so boof :) I missed that 

Have you got the case correct - linux is case sensitive.

Where is the iso?

---

### Post by dfreer on 2009-04-24
```
**cd** /home/luke/documents/ubuntu904/
```

Make sure that you use the "cd" command to change directory. Other than that, type the following into terminal and paste us the results:
```
ls -l /home/luke/documents/
```

---

### Post by lukeinvancouver on 2009-04-24
I should have mentioned that I moved the file from the desktop to the folder entered in Terminal and I should have taken off the brackets with the question marks.

Sorry.

---

### Post by lukeinvancouver on 2009-04-24
> **forestpixie said:**
> 

Have you got the case correct - linux is case sensitive.

Where is the iso?

I knew that Linux is case sensitive but it was a mistake; I capitalized the U (something I don't usually do, hence the mistake)

The directory exists and the file is there


luke@ubuntu:~$ cd /home/luke/documents/ubuntu904
bash: cd: /home/luke/documents/ubuntu904: No such file or directory
luke@ubuntu:~$ cd /home/luke/documents/Ubuntu904
bash: cd: /home/luke/documents/Ubuntu904: No such file or directory

---

### Post by lukeinvancouver on 2009-04-24
> **dfreer said:**
> ```
**cd** /home/luke/documents/ubuntu904/
```

Make sure that you use the "cd" command to change directory. Other than that, type the following into terminal and paste us the results:
```
ls -l /home/luke/documents/
```

luke@ubuntu:~$ ls -l /home/luke/documents/
ls: cannot access /home/luke/documents/: No such file or directory
luke@ubuntu:~$ 

:confused:

---

### Post by lukeinvancouver on 2009-04-24
I shouldn't have said "the directory does exist" because it's obviously me who is wrong not the computer. But there is **a** directory and the file is there.


:D

---

### Post by Elfy on 2009-04-24
start with 

```
ls -l
```

check what name is there - you sure it's not Documents

try 
```
cd ~/Documents
```

---

### Post by MyR on 2009-04-24
typically the "documents" folder has a capital D
/home/luke/Documents

peace

---

### Post by Malalo on 2009-04-24
You could also try

```
locate ubuntu-9.04-desktop-i386.iso
```

---

### Post by lukeinvancouver on 2009-04-24
> **forestpixie said:**
> start with 

```
ls -l
```

check what name is there - you sure it's not Documents

try 
```
cd ~/Documents
```

Wow! I'm learning something. Thank you.

luke@ubuntu:~$ ls -1
Desktop
Documents
Examples
Music
Pictures
Public
Templates
Videos
luke@ubuntu:~$ cd ~/Documents
luke@ubuntu:~/Documents$ ls -1 /home/luke/Documents
Ubuntu904
luke@ubuntu:~/Documents$ 


But what do I do now, please?

---

### Post by lukeinvancouver on 2009-04-24
> **MyR said:**
> typically the "documents" folder has a capital D
/home/luke/Documents

peace

Indeed. Thank you.

---

### Post by lukeinvancouver on 2009-04-24
> **Malalo said:**
> You could also try

```
locate ubuntu-9.04-desktop-i386.iso
```

Thank you.

luke@ubuntu:~$ locate ubuntu-9.04-desktop-i386.iso
/home/luke/.local/share/Trash/files/ubuntu-9.04-desktop-i386.iso
/home/luke/.local/share/Trash/info/ubuntu-9.04-desktop-i386.iso.trashinfo
luke@ubuntu:~$ 

A word of explanation why Ubuntu was in the trash. I was doing something (probably wrong) and lots and lots of windows were loading.

So I just hot the power switch (thinking in good Windows fashion that there was some kind of attack going on). When I powered up again the iso file had disappeared. I didn't think of checking trash until I had downloaded it again. (Btw Linux is 4 times faster than Vista.)

I have since emptied the trash and have a feeling I will be downloading the iso file again.

But then again it shows up in File Browser.

---

### Post by lukeinvancouver on 2009-04-25
I would still very much like to learn how to do an md5sum but gave up for the time being.

I still get this:

luke@ubuntu:~$ cd /home/luke/Documents/ubuntu904/
bash: cd: /home/luke/Documents/ubuntu904/: No such file or directory
luke@ubuntu:~$ 

And it does seem to exist, doesn't it (see above)?

What am I missing?

---

### Post by lukeinvancouver on 2009-04-25
I burned the download to disk and it loads OK.

What are the chances of the download being corrupted?

---

### Post by Elfy on 2009-04-25
> **lukeinvancouver said:**
> I would still very much like to learn how to do an md5sum but gave up for the time being.

I still get this:

luke@ubuntu:~$ cd /home/luke/Documents/ubuntu904/
bash: cd: /home/luke/Documents/ubuntu904/: No such file or directory
luke@ubuntu:~$ 

And it does seem to exist, doesn't it (see above)?

What am I missing?

To do the md5sum on the file in the Documents do

```
md5sum /home/luke/Documents/insertfoldername/name.iso
```

You can use tab to autocomplete - try getting to Docu then tab - it should fill in name - that way you can make sure that you get to the right file and place.

---

### Post by kansasnoob on 2009-04-25
> **lukeinvancouver said:**
> I would still very much like to learn how to do an md5sum but gave up for the time being.

I still get this:

luke@ubuntu:~$ cd /home/luke/Documents/ubuntu904/
bash: cd: /home/luke/Documents/ubuntu904/: No such file or directory
luke@ubuntu:~$ 

And it does seem to exist, doesn't it (see above)?

What am I missing?

Your commands are still not correct. Just **ubuntu904** won't cut it!

I always create a Downloads folder, but it would work the same for Desktop, Documents, etc.

[ATTACH]110982[/ATTACH]

A picture is worth a thousand words:)

You see the file name must be exact, ie: **ubuntu-9.04-desktop-i386.iso**

---

### Post by kansasnoob on 2009-04-25
> **lukeinvancouver said:**
> I burned the download to disk and it loads OK.

What are the chances of the download being corrupted?

I still always select Check disc for defects - always!

[http://www.psychocats.net/ubuntu/images/installingjaunty02.png](http://www.psychocats.net/ubuntu/images/installingjaunty02.png)

---

### Post by lukeinvancouver on 2009-04-25
> **MyR said:**
> typically the "documents" folder has a capital D
/home/luke/Documents

peace

My mistake copying it with the mistake above.

But it didn't work when I spelled it correctly before and it doesn't work now though the error message is different.

I must have made another mistake,

Sorry

---

### Post by lukeinvancouver on 2009-04-25
> **forestpixie said:**
> To do the md5sum on the file in the Documents do

```
md5sum /home/luke/Documents/insertfoldername/name.iso
```

You can use tab to autocomplete - try getting to Docu then tab - it should fill in name - that way you can make sure that you get to the right file and place.

No luck.

luke@ubuntu:~$ luke@ubuntu:~$ cd /home/luke/Documents/ubuntu904
bash: luke@ubuntu:~$: command not found
luke@ubuntu:~$ md5sum /home/luke/Documents/insertfoldername/name.iso
md5sum: /home/luke/Documents/insertfoldername/name.iso: No such file or directory
luke@ubuntu:~$

Doing it with the partial word of Doc and tab yielded this:

luke@ubuntu:~$ cd cd /home/luke/Documents/
bash: cd: cd: No such file or directory
luke@ubuntu:~$

---

### Post by Elfy on 2009-04-25
I would use locate

```
locate *.iso
```

Then when you get the location in the terminal - highlight the location - all of it then type md5sum - then middle mouse button - it will paste the lcoation you highlighted

---

### Post by lukeinvancouver on 2009-04-25
> **forestpixie said:**
> I would use locate

```
locate *.iso
```

Then when you get the location in the terminal - highlight the location - all of it then type md5sum - then middle mouse button - it will paste the lcoation you highlighted

I will do this right away.

Here's the latest try:

luke@ubuntu:~$ cd cd /home/luke/Documents/
bash: cd: cd: No such file or directory
luke@ubuntu:~$ md5sum /home/luke/Documents/ubuntu904/ubuntu-9.04-desktop-i386.iso
md5sum: /home/luke/Documents/ubuntu904/ubuntu-9.04-desktop-i386.iso: No such file or directory


The file is there; I just burned it to disk.

---

### Post by lukeinvancouver on 2009-04-25
> **forestpixie said:**
> I would use locate

```
locate *.iso
```

Then when you get the location in the terminal - highlight the location - all of it then type md5sum - then middle mouse button - it will paste the lcoation you highlighted

Thanks for all your help. It's greatly appreciated. "**Permission denied**"???

luke@ubuntu:~$ locate *.iso
/home/luke/Documents/Ubuntu904/ubuntu-9.04-desktop-i386.iso
luke@ubuntu:~$ /home/luke/Documents/Ubuntu904/ubuntu-9.04-desktop-i386.iso
bash: /home/luke/Documents/Ubuntu904/ubuntu-9.04-desktop-i386.iso: Permission denied
luke@ubuntu:~$

---

### Post by egalvan on 2009-04-25
> **lukeinvancouver said:**
> 

Here's the latest try:

luke@ubuntu:~$[COLOR="Red"] cd cd [/COLOR]/home/luke/Documents/
bash:[COLOR="Red"] cd: cd: [/COLOR]No such file or directory
luke@ubuntu:~$ md5sum /home/luke/Documents/ubuntu904/ubuntu-9.04-desktop-i386.iso
md5sum: /home/luke/Documents/ubuntu904/ubuntu-9.04-desktop-i386.iso: No such file or directory


The file is there; I just burned it to disk.

Why the double [COLOR="Red"]cd[/COLOR] command?

---

### Post by Elfy on 2009-04-25
you don't want to run it - you want to check it

```
md5sum /home/luke/Documents/Ubuntu904/ubuntu-9.04-desktop-i386.iso
```

---

### Post by lukeinvancouver on 2009-04-25
I own the file and I changed the permission to allow read and write.

luke@ubuntu:~$ /home/luke/Documents/Ubuntu904/ubuntu-9.04-desktop-i386.iso
bash: /home/luke/Documents/Ubuntu904/ubuntu-9.04-desktop-i386.iso: Permission denied
luke@ubuntu:~$ 

:confused:

---

### Post by lukeinvancouver on 2009-04-25
> **egalvan said:**
> Why the double [COLOR="Red"]cd[/COLOR] command?

That was a one time mistake, I guess I'm getting kind of tense.
Sorry.

---

### Post by lukeinvancouver on 2009-04-25
> **forestpixie said:**
> you don't want to run it - you want to check it

```
md5sum /home/luke/Documents/Ubuntu904/ubuntu-9.04-desktop-i386.iso
```

I'm afraid I don't understand. Sorry.

I copied / pasted the command from your post

---

### Post by Elfy on 2009-04-25
so did it give you the checksum number?

---

### Post by lukeinvancouver on 2009-04-25
> **egalvan said:**
> Why the double [COLOR="Red"]cd[/COLOR] command?

Ooops, maybe it wasn't a one time mistake. Sorry but one tends to get a bit tense with this.

luke@ubuntu:~$ /home/luke/Documents/Ubuntu904/ubuntu-9.04-desktop-i386.iso
bash: /home/luke/Documents/Ubuntu904/ubuntu-9.04-desktop-i386.iso: Permission denied
luke@ubuntu:~$  cd /home/luke/Documents/
luke@ubuntu:~/Documents$ ls
from-desktop-Ubuntu904  MD5SUMS.desktop  Ubuntu904
luke@ubuntu:~/Documents$

---

### Post by lukeinvancouver on 2009-04-25
> **forestpixie said:**
> so did it give you the checksum number?

No

:(

---

### Post by Elfy on 2009-04-25
Did it do anything? Was there an error reported?

---

### Post by boof1988 on 2009-04-25
> **lukeinvancouver said:**
> I will do this right away.

Here's the latest try:

luke@ubuntu:~$ cd cd /home/luke/Documents/
bash: cd: cd: No such file or directory
luke@ubuntu:~$ md5sum /home/luke/Documents/ubuntu904/ubuntu-9.04-desktop-i386.iso
md5sum: /home/luke/Documents/ubuntu904/ubuntu-9.04-desktop-i386.iso: No such file or directory


The file is there; I just burned it to disk.

When you are trying to find a file or trying to *cd* to that directory, one helpful hint is to use <Tab>-completion.  I'll give a quick idea on what it does and how it may help you with your task of performing an *md5sum* check of a file.

Let us assume you are trying to *cd* into the directory where the *.iso* file (the *ubuntu-9.04-desktop-i386.iso* file) is located.

Do the following in the Terminal...

[LIST=1]
[*]Type in the following...
```
cd /ho
```
[*]Then press the <Tab> key
[*]The Terminal should now have added some more letters so that the following is displayed...
```
cd /home/
```
[*]Now type in the first letter of your username (I assume it is l for you) and then press <Tab> again and the Terminal should complete your username and should display the following...
```
cd /home/luke/
```
[*]Now press the <Tab> key twice and then the Terminal will display all the files located in your home directory (mine looks like the following)...
```
bs@gx110:~$ cd /home/bs/
.cache/           .fontconfig/      .gstreamer-0.10/  .lyrics/
.clamtk/          .gconf/           .gvfs/            .mozilla/
.config/          .gconfd/          gx110data/        .thumbnails/
.dbus/            .gnome2/          .listen/          .update-notifier/
Desktop/          .gnome2_private/  .local/
```
[*]Now look at the files/directories listed and type the first letter or two or three of the directory you want to navigate to and then press <Tab> again...
[*]Continue this until the file path following the "cd" is the directory containing the *.iso* file that you want to check...
[*]Press enter and the Terminal should now show that you are in the directory where the *.iso* file is located (I am in the gx110data directory even thought I don't have any .iso files in it)...
```
bs@gx110:~$ cd /home/bs/gx110data/
bs@gx110:~/gx110data$
```
[*]Now type in the following and press <Enter>.  This will display the files in the current working directory.  The *.iso* file should be one of the files listed.
```
ls -al
```
[*]Now type the following and then use <Tab>-completion to finish the line (it should finish the filename *ubuntu-9.04-desktop-i386.iso*) and then press enter...
```
md5sum ub
```
[/LIST]

---

### Post by lukeinvancouver on 2009-04-25
> **boof1988 said:**
> When you are trying to find a file or trying to *cd* to that directory, one helpful hint is to use <Tab>-completion. .... 

Thank you so much for all that work. I really appreciate it.

And Hallelujah!!!!

luke@ubuntu:~$ cd /home/
luke@ubuntu:/home$ cd /home/luke/
luke@ubuntu:~$ 
Display all 2105 possibilities? (y or n)
luke@ubuntu:~$ cd /home/
luke@ubuntu:/home$ cd /home/luke/
luke@ubuntu:~$  cd /home/luke/
luke@ubuntu:~$ cd /home/luke/Documents
luke@ubuntu:~/Documents$ ls
from-desktop-Ubuntu904  MD5SUMS.desktop  Ubuntu904
luke@ubuntu:~/Documents$ cd Ubuntu904
luke@ubuntu:~/Documents/Ubuntu904$ ls
md5sum-instructions.odt  ubuntu-9.04-desktop-i386.iso
luke@ubuntu:~/Documents/Ubuntu904$ md5sum /home/luke/Documents/Ubuntu904/ubuntu-9.04-desktop-i386.iso
66fa77789c7b8ff63130e5d5a272d67b  /home/luke/Documents/Ubuntu904/ubuntu-9.04-desktop-i386.iso
luke@ubuntu:~/Documents/Ubuntu904$ 

66fa77789c7b8ff63130e5d5a272d67b

---

### Post by CatKiller on 2009-04-25
> **lukeinvancouver said:**
> luke@ubuntu:~$ /home/luke/Documents/Ubuntu904/ubuntu-9.04-desktop-i386.iso

Slow down. This isn't life-or-death. There's no need to be tense.

What you're doing with this command really isn't what you want to be doing. The general format of a command-line command is ```
<command> <thing>
```Sometimes it might be ```
<command> <options> <thing>
``` or ```
<command> <thing> <other thing>
``` and sometimes the <thing>s are implied, so just ```
<command>
``` will work.

In this case, with that command above, you think you're doing something to <thing> but since that's all you've put and ```
<thing>
``` makes no sense, your path to your iso is being interpreted as ```
<command>
``` But that iso file isn't executable (it doesn't have execute permissions) which means that your command doesn't work, and so the Terminal gives you an error and its best guess at what the error means.

Now read the commands that people have given you **carefully**. Tab-completion is brilliant, and should be used all the time. boof's description is a good one.

Now, as a practice, we'll **c**hange **d**irectory into the directory that has your iso (<command> <thing>). You'll want to type 

cd Doc<Tab>Ubu<Tab>

(note the capital U)

which will give you ```
cd Documents/Ubuntu904
```ls should now show you that that directory contains a file called ubuntu-9.04-desktop-i386.iso. You want to check the MD5 sum of that file (<command> <thing>). So you'll type 

md5<Tab> ubu<Tab>

(note the space and the lower-case u)

which will give you ```
md5sum ubuntu-9.04-desktop-i386.iso
```When that's run, it should spit out a long number that you can compare with what you were expecting the MD5 sum to be.

---

### Post by lukeinvancouver on 2009-04-25
Thank you ALL so very, very much for your help and not least for the patience you have shown towards a total rookie.

:KS
:popcorn:
:)

I can't compare it right now top the md5sum at Ubuntu because the page refuses to load. (I'll again try a little later.)

---

### Post by lukeinvancouver on 2009-04-25
> **CatKiller said:**
>  There's no need to be tense.



"No need to be tense": True enough but firstly I have been trying for more than a day to do this and secondly we are all people with different ways.

Thank you very much for the detailed explanation. It will surely be useful for me in the future.

---

### Post by Elfy on 2009-04-25
66fa77789c7b8ff63130e5d5a272d67b from the hash page
66fa77789c7b8ff63130e5d5a272d67b from your post

Looks fine to me :)

Good luck and have fun :)

---

### Post by lukeinvancouver on 2009-04-25
> **forestpixie said:**
> 66fa77789c7b8ff63130e5d5a272d67b from the hash page
66fa77789c7b8ff63130e5d5a272d67b from your post

Looks fine to me :)

Good luck and have fun :)

To me too; I just managed to get to the page.

66fa77789c7b8ff63130e5d5a272d67b
66fa77789c7b8ff63130e5d5a272d67b

Thank you very much and in spite of the tension I am having fun because finally it seems I'm going to get somewhere with Linux.

I've tried several distros in the last 2 or 3 years and always gave up at some point.

But with Ubuntu I think I'm going to make it not least because of this wonderful forum here.

Thank you all again!!!

---

### Post by Elfy on 2009-04-25
Make sure you check the cd integrity form the boot menu - when you get to boot it - make sure all is well before you try to install it.

---

### Post by lukeinvancouver on 2009-04-25
> **forestpixie said:**
> Make sure you check the cd integrity form the boot menu - when you get to boot it - make sure all is well before you try to install it.

Thanks for reminding me. I was going to to do am md5sum check of the CD. I printed the instructions from the Ubuntu page.

Should I do both or just the check at bootup?

---

### Post by CatKiller on 2009-04-25
> **lukeinvancouver said:**
> Should I do both or just the check at bootup?

They're the same thing. The cd check is a file-by-file MD5 hash check.

You need to do the check on the iso to make sure you aren't repeatedly burning a bad download, and the check of the cd to make sure that you haven't got a bad burn. But checking the files on the cd once it's burned and using the built-in cd check are equivalent.

---

### Post by lukeinvancouver on 2009-04-25
> **CatKiller said:**
> They're the same thing. The cd check is a file-by-file MD5 hash check.

You need to do the check on the iso to make sure you aren't repeatedly burning a bad download, and the check of the cd to make sure that you haven't got a bad burn. But checking the files on the cd once it's burned and using the built-in cd check are equivalent.

Thank you very much

---

### Post by presence1960 on 2009-04-25
> **lukeinvancouver said:**
> I would still very much like to learn how to do an md5sum but gave up for the time being.

I still get this:

luke@ubuntu:~$ cd /home/luke/Documents/ubuntu904/
bash: cd: /home/luke/Documents/ubuntu904/: No such file or directory
luke@ubuntu:~$ 

And it does seem to exist, doesn't it (see above)?

What am I missing?

You are probably entering the .iso name incorrectly, my downloaded .iso is named ```
ubuntu-9.04-desktop-amd64.iso 
``` not ubuntu904 as you have typed into the terminal. Unless you have edited the name of the file after downloading this may be your problem or at least one of your problems.

---

### Post by lukeinvancouver on 2009-04-25
> **presence1960 said:**
> You are probably entering the .iso name incorrectly, my downloaded .iso is named ```
ubuntu-9.04-desktop-[COLOR="Red"]amd64[/COLOR].iso 
``` not ubuntu904 as you have typed into the terminal. Unless you have edited the name of the file after downloading this may be your problem or at least one of your problems.

Thank you for your help.

I would have thought that [COLOR="Red"]amd64[/COLOR] stands for an  AMD 64 bit machine. No? I have an Intel 32 bit.

The folder name Ubuntu904 was chosen by me as I do not know if one is [COLOR="Red"]allowed to include periods in a file name[/COLOR].

The file name was not changed and the problem was solved a few hours ago.

See my post **Hallelujah!!!**

But I must add that I've had Ubuntu for only about two weeks. It's not the first time I try to learn how to walk in Linux but previously I gave up with several distros over the last two or three years.

I really have the feeling that this time I'll make it to Linux for good.

It's been a wonderful two weeks of learning! 

And when a problem was resolved I had learned much more than just how to resolve it.

I even dared offering some advice to somebody else who had a problem similar to what I had and which was resolved because of the kind efforts of sombody typing a huge amount of detailed instructions because he has the same hardware and had had the same problem.

My problem got resolved because of his help. 

The person's who I tried to help tried what I told him to do and alas, it didn't work. A bit arrogant maybe, a newbie offering advice. But I solved a similar problem with the help of somebody I'll never meet in person. So I had a go at it and it didn't help. (It didn't do any damage either.)

Or **today**: As people were kindly steering me towards a solution they taught me a lot about certain commands and what to watch out for, e.g. Documents and NOT documents.

And the tone. 

I'm used to political chatboards and although I stopped insulting people years ago because it's counterproductive (and not nice) it is common, even personal insults from people who have never met you.

Not here. How refreshing!

One silly question (after havin wasted a lot of time on BBS, but it's been a long time since): [COLOR="Red"]How can I fetch a link, i.e. go to another page without losing my  text?[/COLOR]

Would Ctrl + Enter open another browser window?

[SIZE="5"]Thank you all so much. It's wonderful to be here.[/SIZE]

---

### Post by lukeinvancouver on 2009-04-25
I wrote: "I would have thought that amd64 stands for an AMD 64 bit machine."

Sorry it was only after posting that I read that it isthe file on your machine.

Oooops

:P

---

### Post by presence1960 on 2009-04-25
Excellent! Glad you got it working. If you stick it out you will learn. There are various ways to learn, such as getting in there rolling the sleeves up and doing, sometimes having to fix what you try to do. Another is reading the threads in here and trying what you find after absorbing the knowledge. Another is by asking questions. Another is reading. here are a couple links [http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)  to download a free Ubuntu pocketguide & [http://www.psychocats.net/](http://www.psychocats.net/)  for some great info. I found it helpful to find someone in my area more experienced at Linux to help me out on a casual basis. Sometimes face to face help is far better than written word. Hang in there and suck it all up, it is here for us all.

---

### Post by CatKiller on 2009-04-25
> **lukeinvancouver said:**
> The folder name Ubuntu904 was chosen by me as I do not know if one is [COLOR=Red]allowed to include periods in a file name[/COLOR].

Yes, you can. The only character in a filename that Linux can't cope with is /. Control characters, like ?, can be in a filename, but they are "escaped" with a \, meaning that you tell it to ignore what the character means and just treat it as a character. Like

```
mplayer Blue\ Oyster\ Cult\ -\ \(Don\'t\ Fear\)\ The\ Reaper.mp3
```

Tab-completion means that you don't need to bother typing all those \s.

> One silly question (after havin wasted a lot of time on BBS, but it's been a long time since): [COLOR=Red]How can I fetch a link, i.e. go to another page without losing my  text?[/COLOR]

Would Ctrl + Enter open another browser window?

Normally, middle-clicking on a link in Firefox will open it in a new tab. Ctrl-T will open a new tab. Ctrl-N opens a new window.

---

### Post by boof1988 on 2009-04-25
> **CatKiller said:**
> Normally, **[COLOR="Blue"]middle-clicking on a link[/COLOR]** in Firefox will open it in a new tab. Ctrl-T will open a new tab. Ctrl-N opens a new window.

Thanks for the tip (in blue-bold).  I usually use <Right-Click> then "Open Link in New Tab".  Now (if I can remember) I can do it with one click instead of two.

---

### Post by lukeinvancouver on 2009-04-25
> **presence1960 said:**
> Excellent! Glad you got it working. If you stick it out you will learn. There are various ways to learn, such as getting in there rolling the sleeves up and doing, sometimes having to fix what you try to do. Another is reading the threads in here and trying what you find after absorbing the knowledge. Another is by asking questions. Another is reading. here are a couple links [http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)  to download a free Ubuntu pocketguide & [http://www.psychocats.net/](http://www.psychocats.net/)  for some great info. I found it helpful to find someone in my area more experienced at Linux to help me out on a casual basis. Sometimes face to face help is far better than written word. Hang in there and suck it all up, it is here for us all.

Some of the things you mention,I've done. Others are on my list.

Thanks again

---

### Post by lukeinvancouver on 2009-04-25
> **boof1988 said:**
> Thanks for the tip (in blue-bold).  I usually use <Right-Click> then "Open Link in New Tab".  Now (if I can remember) I can do it with one click instead of two.

Thanks but just to be sure: Say I'm composing a post. I want to link to another url in my post but I have to go there to copy the url. I don't want to lose the text I've already typed.

Would the back key always get me back?

Surely a dumb question. If so please ascribe it to old age.

:D

---

### Post by lukeinvancouver on 2009-04-25
> **CatKiller said:**
> . Ctrl-T will open a new tab. Ctrl-N opens a new window.

Great. Thank you again.

:D

---

### Post by lukeinvancouver on 2009-04-25
Excuse this test please. I am trying to link to a particular page.

[http://ubuntuforums.org/showthread.php?t=1131829](http://ubuntuforums.org/showthread.php?t=1131829)**

---

### Post by lukeinvancouver on 2009-04-26
Sorry one more test.

Thank you for your patience.

[http://ubuntuforums.org/showthread.php?t=1136203](http://ubuntuforums.org/showthread.php?t=1136203)

---

### Post by CatKiller on 2009-04-26
> **lukeinvancouver said:**
> Would the back key always get me back?

It doesn't always. When the forums been having server problems and a post times out then it just eats the text of your post. That can be annoying.

I use tabs a lot. I've got the tab bar to show even if there's only one tab open so that I can just double-click on the tab bar to open a new tab to hunt information down. I've also got the search box set to put the results in a new tab. That's handy too.

---

### Post by lukeinvancouver on 2009-04-30
> **CatKiller said:**
> It doesn't always. When the forums been having server problems and a post times out then it just eats the text of your post. That can be annoying.

I use tabs a lot. I've got the tab bar to show even if there's only one tab open so that I can just double-click on the tab bar to open a new tab to hunt information down. I've also got the search box set to put the results in a new tab. That's handy too.

Thank you
:P

---

### Post by freeediver on 2009-05-29
I am haviing the same problem doing the md5 check.
I found my file but is tell me denied access.
One thing I notice about your command is whenever you type 9.04
you are actually typing 904, perhaps the "dot" makes a difference??
After reading ever post I see that this omission was caught.
I am having the same problems that you did but my file is on my desk top
I use the if it suggestion and it popped right up.
I have tried substituting "desktop" and following your suggestions 
but I am getting no where or permission denied.
I'm still stuck.
[COLOR="Red"]**It works, Thanks Boof1988**[/COLOR]

---

