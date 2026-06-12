---
title: "Places -&gt; Documents, will not open"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by psyk117 on 2009-11-11
I am having a lot of trouble here... when I do the Places -> Documents, the little thing on the task bar appears, but it never opens, and the little thing disappears. 
Help!
much thanks, psyk117

---

### Post by Rayve on 2009-11-11
Can you get into any other location via the Places menu?  Maybe Places > Home?

---

### Post by psyk117 on 2009-11-11
I can't get into anything under Places

---

### Post by psyk117 on 2009-11-11
help?

---

### Post by psyk117 on 2009-11-11
so this is what free customer support is like... yay me...

---

### Post by Linux&amp;Gsus on 2009-11-11
If you don't like the free customer support then go and pay for some support.

Besides, read your first post again and think very hard how you would answer that.
How about a little better description of what you are doing?

Now, how about opening a terminal and try this:
```
ls -l
```

And what happens in the terminal when you type:
```
cd ~/Documents
```

The first command shows all files and folders in the current folder you are in, which is your /home when you just opened the terminal. It also shows the owner information for every file and folder.

The 2nd command should navigate you into your "Documents" folder.

Post output of both commands here, please.

Cheers,
L&G

---

### Post by psyk117 on 2009-11-11
I apologize.. I'm just a little on edge... I've had smooth sailing since 8.04 Hardy Heron

anyway.
first:
total 5996
drwxr-xr-x  2 psyk117 psyk117    4096 2009-01-19 20:03 Bleh
drwxr-xr-x  3 psyk117 psyk117    4096 2009-11-08 00:52 Desktop
drwxr-xr-x  2 psyk117 psyk117   36864 2009-11-02 13:38 Documents
-rw-r--r--  1 psyk117 psyk117    4652 2009-03-25 22:14 Ember_to_inferno_lead~
-rw-r--r--  1 psyk117 psyk117       1 2009-03-25 22:07 Ember_to_inferno _rythmn~
lrwxrwxrwx  1 psyk117 psyk117      26 2009-01-12 09:56 Examples -> /usr/share/example-content
-rw-r--r--  1 psyk117 psyk117 1645685 2009-05-16 18:35 Firefox_wallpaper.png
-rw-r--r--  1 psyk117 psyk117   35876 2009-06-11 19:31 FreeCol.log
-rw-r--r--  1 psyk117 psyk117 1707856 2001-09-25 15:05 InstMsiA.Exe
-rw-r--r--  1 psyk117 psyk117     812 2009-02-09 20:35 log.txt
drwxr-xr-x 13 psyk117 psyk117    4096 2009-09-17 23:14 Music
-rwxr-xr-x  1 psyk117 psyk117   53760 2009-05-02 03:31 photo2.jpg.exe
drwxr-xr-x  6 psyk117 psyk117    4096 2009-11-04 20:23 Pictures
-rw-------  1 psyk117 psyk117 2512896 2003-08-20 06:06 PTEditor17.msi
drwxr-xr-x  2 psyk117 psyk117    4096 2009-01-12 18:02 Public
-rw-r--r--  1 psyk117 psyk117   65536 2002-01-05 07:46 Setup.Exe
-rw-------  1 psyk117 psyk117      41 2003-08-20 06:05 Setup.Ini
drwxr-xr-x  2 psyk117 psyk117    4096 2009-01-12 18:02 Templates
drwxr-xr-x  3 psyk117 psyk117    4096 2009-08-23 04:26 Videos
-rw-r--r--  1 psyk117 psyk117    1806 2009-02-27 08:16 We Fight (for your pleasure)~

and second:
just changes
psyk117@psyk117-desktop:
to
psyk117@psyk117-desktop:~/Documents$

I feel so stupid... I am no good at this stuff

---

### Post by psyk117 on 2009-11-11
to clarify my problem:
I go to Places -> Documents.
I click on Documents.
it looks like the window is going to come up.
the window never appears.
same deal for everything under Places ->

---

### Post by Linux&amp;Gsus on 2009-11-11
No worries. Just saying, a friendly tone usually speeds up help ;)

Anyways. I kinda suspected that ownership or user rights weren't correct. But all that seems fine.
So, when you "do the Places -> Documents" I assume you mean that you want to navigate to your folder called "Documents" in your file browser. The 2nd command in the terminal did exactly that, well, just in the terminal.
I believe the file browser in Ubuntu (I'm using Kubuntu) is called Nautilus, right? Try in the terminal
```
nautilus
```
It should open that thing or give error messages if it can't open it.

Oh, and don't feel stupid! This is about as much as I can think of right now. I hope it'll give some insight in the issue. Not being an all-knowing expert doesn't mean being stupid. ;)

Cheers,
L&G

---

### Post by psyk117 on 2009-11-11
I typed in nautilus (I never in my life had to spell that word manually), and I got this output:
(nautilus:14856): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Segmentation fault

I'm guessing it's bad... very bad..

---

### Post by Linux&amp;Gsus on 2009-11-11
> **psyk117 said:**
> to clarify my problem:
I go to Places -> Documents.
I click on Documents.
it looks like the window is going to come up.
the window never appears.
same deal for everything under Places ->

See, I assumed wrong. Can you open Nautilus at all?

---

### Post by Linux&amp;Gsus on 2009-11-11
> **psyk117 said:**
> I typed in nautilus (I never in my life had to spell that word manually), and I got this output:
(nautilus:14856): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Segmentation fault

I'm guessing it's bad... very bad..

Ooops, I was too slow.
Well, you could have just copied and pasted it. ;)

But yeah, that looks like it is your problem. What is best to do now I better leave to some one more knowledgeable.

---

### Post by psyk117 on 2009-11-11
thank you for your insight.
I will await more responses.

---

### Post by skullsk8er on 2009-11-11
> **psyk117 said:**
> I apologize.. I'm just a little on edge... I've had smooth sailing since 8.04 Hardy Heron

anyway.
first:
total 5996
drwxr-xr-x  2 psyk117 psyk117    4096 2009-01-19 20:03 Bleh
drwxr-xr-x  3 psyk117 psyk117    4096 2009-11-08 00:52 Desktop
drwxr-xr-x  2 psyk117 psyk117   36864 2009-11-02 13:38 Documents
-rw-r--r--  1 psyk117 psyk117    4652 2009-03-25 22:14 Ember_to_inferno_lead~
-rw-r--r--  1 psyk117 psyk117       1 2009-03-25 22:07 Ember_to_inferno _rythmn~
lrwxrwxrwx  1 psyk117 psyk117      26 2009-01-12 09:56 Examples -> /usr/share/example-content
-rw-r--r--  1 psyk117 psyk117 1645685 2009-05-16 18:35 Firefox_wallpaper.png
-rw-r--r--  1 psyk117 psyk117   35876 2009-06-11 19:31 FreeCol.log
-rw-r--r--  1 psyk117 psyk117 1707856 2001-09-25 15:05 InstMsiA.Exe
-rw-r--r--  1 psyk117 psyk117     812 2009-02-09 20:35 log.txt
drwxr-xr-x 13 psyk117 psyk117    4096 2009-09-17 23:14 Music
-rwxr-xr-x  1 psyk117 psyk117   53760 2009-05-02 03:31 photo2.jpg.exe
drwxr-xr-x  6 psyk117 psyk117    4096 2009-11-04 20:23 Pictures
-rw-------  1 psyk117 psyk117 2512896 2003-08-20 06:06 PTEditor17.msi
drwxr-xr-x  2 psyk117 psyk117    4096 2009-01-12 18:02 Public
-rw-r--r--  1 psyk117 psyk117   65536 2002-01-05 07:46 Setup.Exe
-rw-------  1 psyk117 psyk117      41 2003-08-20 06:05 Setup.Ini
drwxr-xr-x  2 psyk117 psyk117    4096 2009-01-12 18:02 Templates
drwxr-xr-x  3 psyk117 psyk117    4096 2009-08-23 04:26 Videos
-rw-r--r--  1 psyk117 psyk117    1806 2009-02-27 08:16 We Fight (for your pleasure)~

and second:
just changes
psyk117@psyk117-desktop:
to
psyk117@psyk117-desktop:~/Documents$

I feel so stupid... I am no good at this stuff

like L&G said, being a beginner doesn't mean  u are stupid, u just don't have enough experience.the second part is right as well, a friendly tone helps a lot. And besides i have solved every problem i had with my ubuntu searching this forum.it;s just great, really.

I can't help you with the output of your first command.However the output from the second command came out great.the ~/Documents$ in psyk117@psyk117-desktop:~/Documents$ means that u are now in home directory(alias ~ )/Documents.So you are finally inside your Documents folder.Which means that u can basicly reach any folder or file running terminal commands, so your problem with click-to-get-to-folder- problem can be fixed.good luck :)

---

### Post by psyk117 on 2009-11-11
how can I see all of my documents though?
I get confused with just text...

---

### Post by skullsk8er on 2009-11-11
> **psyk117 said:**
> how can I see all of my documents though?
I get confused with just text...

u can see the containts of every directory using the ls -p(a flag for the ls commnand).
and u can translate the output as follows
-direcorys eg: music/
-files : eg : letter_to_mom.odt, list.tar.gz(ubuntu archive)

to open a file it depends of the file.
to open up a text file : gedit letter_to_mom.odt or acroread "Agile Web Development with Rails 3rd Ed~tqw~_darksiderg.pdf" to open up a pdf(if u have acrobat reader installed)
an important thig would be that u must be in a direcory to open up a file form within it, or to specify the program that opens the file and the path of the file, like in the command acroread "Agile Web Development with Rails 3rd Ed~tqw~_darksiderg.pdf"

let me know if u nailed it :)

---

### Post by skullsk8er on 2009-11-11
and the dude was complaining about this brilliant customer support,now he's not even answering :)) shamne :) Ubuntu forum 4ever!!

---

### Post by Linux&amp;Gsus on 2009-11-11
Well, it might be helpful if someone could help with the GUI side of the issue.
I just don't know if it help to re-install Nautilus or if there is a potential to do some harm with it, as in messing with Windows Explorer in Windows will give trouble. I just don't know how that is handled in Linux. So, I hope someone knowledgeable will show up and give the right hint.

However, I think trying to update the system can't hurt, it might even do some magic and fix the issue. You'll never know.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by psyk117 on 2009-11-11
I did the update.
still having the problem  :(

---

### Post by psyk117 on 2009-11-11
sorry guys, I fell asleep trying to figure this all out.

---

### Post by lotharmat on 2009-11-11
Is it possible to uninstall Nautilus and then install it again?

There are other filemanagers about as well 

[INDENT]PCMan[/INDENT]

can be added from the add/remove software in Karmic

---

### Post by Rayve on 2009-11-11
If it's a permissions issue, would 

```

gksudo nautilus

```

work?  

Big note of warning: when (if) you run nautilus like this, you are running it as "sudo" or basically root user, and you have free reign to cause chaos.  Be careful what you do while in sudo, or gksudo (graphical sudo)!

Navigate to your /home folder - you will likely start out in "root", so on the left side of the window, choose "File System" and then the "home" folder, and then your name.  If you are able to see your folders, you may notice a sort of "X" symbol (in Ubuntu, anyway) which denotes that they are locked.  You can right-click them and then choose "Properties" and check the Permissions - what does it say for "owner" (which should be your name)?  Change it to "create and delete files" for the folders in your /home directory you are sure you should have such access to.

Alternatively, you can uninstall and reinstall nautilus to see if that helps. 

From this thread ([http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=844990](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=844990)), edited slightly: 

remove nautilus (enter "sudo apt-get remove --purge nautilus" without the quotes in a terminal) then re-install it ("sudo apt-get install nautilus" without the quotes)

Hopefully some of this helps!

---

### Post by Karmatica on 2009-11-11
I also am having the same problems. I was running 9.04 and after upgrading nautilus stopped working. I tried new users, uninstalling and reinstalling nautilus. So I just did a complete reinstall and nautilus worked, well sort of I can get to places no problem and it will work through terminal as well but still get the error message:

Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

Then I allowed update manager to update and then after nautilus no longer worked. So I am back to step one and reinstalled Ubuntu 9.10 and am going to update each of the 86 items, and see which update messes things up I believe it might be one of the following, Adobe Flash, Brasero, rythmbox or possibly one of the codecs. I will keep you posted and see what happens.

---

### Post by RobinJ1995 on 2009-11-11
install dolphin from the software center and type that in the terminal, does that work?

---

### Post by philinux on 2009-11-11
Do this, copy and paste the command into a terminal.

```
rm -r ~/.gconf/apps/nautilus/
```

Logout then login and try places>documents again.

The above code removes the nautilus settings. This folder will be recreated when you do Edit>Prefs in nautilus.

---

### Post by philinux on 2009-11-11
If the above does not work then do this.

```
sudo apt-get remove --purge nautilus

Then

sudo apt-get install nautilus


```

---

### Post by Zoot7 on 2009-11-11
Reinstalling it is the way I'd go too
Failing that I'd say the most likely problem is there's probably a dependency gone awry that directly affects nautlius.

A useful command is
```
aptitude why-not nautilus
```
That'll investigate if there's any package conflicting with nautilus.

---

### Post by psyk117 on 2009-11-11
I am so frustrated!
nothing is working.
I tried removing and re-installing. nothing
I don't even want to try gksudo, afraid I'll mess everything up.
Nothing else is working...

---

### Post by Karmatica on 2009-11-11
ok so heres the thing i did the new install then did each update separately and other then the one warning:

(nautilus:17107): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

Nautilus still worked...until i put a cd which only had MP3's and Wma's on it. nad then Nautilus gave me this warning:

(nautilus:17182): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:17182): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:17182): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:17182): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Segmentation fault


 I added the plugin's neccessary to play them, then i got this warning:

(nautilus:18495): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:18495): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:18495): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:18495): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Segmentation fault

I have tried reinstalling nautilus from synaptic package manager to no avail  but i am going to try the last 2 suggestions and see if that helps. another thing i have noticed is that under places 2 cdroms appear I only have 1 drive

---

### Post by psyk117 on 2009-11-11
update:
I am now using PCMan.
not as convenient, but it gets the job done...

---

### Post by Karmatica on 2009-11-11
ok i also tried what was suggested none of which worked going to try pcman then

---

### Post by Zoot7 on 2009-11-11
Did the command I posted yield anything of interest?

---

### Post by psyk117 on 2009-11-11
it told me that nautilus had no reason to be deleted

---

### Post by Karmatica on 2009-11-12
Same result for me. On the upside I found out what seems to be causing the issue for me, mind you fixing it on the other hand?
After getting the nautilus has no conflicts message and then purging nautilus and using dolphin instead...nothing worked so I had to do a new fresh reinstall .
The culprit it seems is the burned CD I have with MP3's on it because nautilus works when the CD is not in the drive but it won't work when it is in the drive any idea on how to fix that? is it possible to install 2 file managers at the same time?

---

### Post by philinux on 2009-11-12
> **Karmatica said:**
> Same result for me. On the upside I found out what seems to be causing the issue for me, mind you fixing it on the other hand?
After getting the nautilus has no conflicts message and then purging nautilus and using dolphin instead...nothing worked so I had to do a new fresh reinstall .
The culprit it seems is the burned CD I have with MP3's on it because nautilus works when the CD is not in the drive but it won't work when it is in the drive any idea on how to fix that? is it possible to install 2 file managers at the same time?

you can have as many file managers as you like. Same with text editors and browser etc,etc.....

---

### Post by wojox on 2009-11-12
If you have a Cd/Dvd in the drive it will screw nautilus up. Don't know why.

---

### Post by Riihma on 2009-11-12
Thanks Karmatica for CD-info,

I have tried to get Nautilus working three days - and that all was caused by LCD monitor cd in cd/dvd station! 

Riihma

---

### Post by philinux on 2009-11-12
Have you guys with problem tried disabling compiz.

System>prefs>appearance>desktop effects> None

---

### Post by tunznath on 2009-11-19
I have the same problem after trying to backup a dvd using K9copy, deleted K9 copy and at least got my desktop background back but then couldnt get anything from places> *anything* now using Thunar (thanks to Slumbergod for helping) which works - anyone know what is up with nautilus?
Karmic Bug?
I kept getting program nautilus has unexpectedly crashed

---

### Post by saisho on 2009-11-21
Try to follow the solution in [http://ubuntuforums.org/showthread.php?t=1322002&referrerid=183448](http://ubuntuforums.org/showthread.php?t=1322002&referrerid=183448) 
It did solve the problem for me.

---

