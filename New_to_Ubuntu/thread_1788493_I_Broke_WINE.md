---
title: "I Broke WINE"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by donnagarnet on 2011-06-22
I've been using Ubuntu for a year, but because I'm a casual user who gets a headache from "Linux-tech" lingo, I decided to post in "Beginners".

I have no idea what I did wrong.  I downloaded WINE right from the included software catalog.  

I've been trying to install Adobe Digital Editions with WINE. Whenever I try to install it (or anything else) with WINE. I get the 'options' box which already has "Install with WINE Program Loader".

After it installs, I always get this message:

"The file '/tmp/setup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

There is an "OK" button at the bottom.

Does anyone know what I've done wrong & how I can correct it?

Thanks.

---

### Post by anoop999 on 2011-06-22
Your downloaded program might not have permission to execute.
You need to explicitly give the program permission, using a command such as:

chmod +x /tmp/setup.exe

or by right-clicking on the file in Nautilus file manager, selecting 'Properties' then 'Permissions' in the menu, and clicking the option to 'allow the file to execute as a program'.

---

### Post by donnagarnet on 2011-06-22
It Thanks for your help, but ADE doesn't show up in the File Manager.  

It does show up in Firefox  Tools> Downloads, but if I click on it, I just get the "not executable" message again.

chmod +x /tmp/setup.exe   Where should I enter that?  I tried typing it into the teminal, with no success.

Thanks for your patience.

---

### Post by Vansch76 on 2011-06-22
Donna

It doesn't sound like wine is broken

open a terminal
type cd /temp

this should put you in the directory with the setup file

type ls to display a list of files in this directory.

you should see the setup.exe in the listing.

type sudo chmod +x/setup.exe 
press enter
enter your sudo password

the property should have been changed after doing this

if you type ls again the file setup.exe should have changed color. 

if you run the install program again it should execute correctly.

let us know how it goes.

Vanessa

---

### Post by amanchesterman on 2011-06-23
Vannessa's advice is right, except that the file you downloaded may not be in the /temp folder.

Open Firefox and click on Edit > Preferences > Downloads. It should tell you where downloaded files are stored. (On my machine they are in the 'Downloads' folder ... surprise, surprise!)

Then you need to navigate to that folder. You can do it in the terminal as Vanessa says or you should be able to do it with Nautilus.

John

---

### Post by ExileAmongYou on 2011-06-23
It sounds like the file is going into the /tmp/ folder because when you're downloading it from the website, you're opening it instead of saving it.
 
If you can't find the setup.exe file in your tmp folder, go back to the website you downloaded it from, right-click on the download link and choose "Save link as...". Save the setup.exe file somewhere that makes sense to you (maybe on your desktop?), then right click on it, go to Permissions and tick the box that says "Allow executing file as program".

Be warned, though, that WINE can't always get all windows programs to install and run properly.

---

### Post by grahammechanical on 2011-06-23
There is another way to install Windows programs through wine. It might work better. Look for the program called Uninstall Wine Software. Click on it and it loads an Add/Remove programs utility. That is right, to install a program in Wine you load the uninstall utility. A better name is needed. In that utility you will see a button called Install. Click on it and you will get a standard Windows browse/open type dialog. Browse to where the program has downloaded and select setup.exe.

I find that this works better for me.

Regards.

---

### Post by donnagarnet on 2011-06-25
I downloaded ADE again, saved it to 'Downloads', then tried what ExileAmongYou suggested.

In reply, I received this message "Unable to elevate to administrative rights, error 1".

Then I tried what Grahmmechanical suggested & got the same message.

Thanks so much, kids.

---

### Post by yetiman64 on 2011-06-25
Hi donnagarnet, check out the attached screenshot, ADE in wine on my Lucid desktop, with a desktop launcher.
 
Once downloaded, I went into to the downloads folder (check browser preferences for where that is on your install - here it is /home/<my-username>/Downloads) and right clicked the install file > Properties > Permissions > Ticked - Allow executing file as program. 
 
Then I basically followed grahammechanical's post and it installed. It sounds as though you may be missing the permissions step
> It Thanks for your help, but ADE doesn't show up in the File Manager.  
 
It does show up in Firefox  Tools> Downloads, but if I click on it, I just get the "not executable" message again. Go into firefox > Edit > Preferences > General Tab and check which folder on your install your downloads are set for. Then in a nautilus window go to that folder and change the file executable bit with the instructions given above and in earlier posts.
 
There was no need to elevate privileges to install it here. Worth another try :), Regards, yetiman64

---

### Post by donnagarnet on 2011-06-25
Thanks, yetiman64.  I tried what you suggested, & got the "Unable to elevate administrative rights" message again.  

Out of curiosity, I used your method to install the "Kindle for PC" app & that worked like a charm (Well, it's on my desktop but I haven't tried it yet).

Is it possible I screwed up something when I first installed Ubuntu (Lucid)?  I've been having massive problems with music players & the eBook viewer as well.

)

---

### Post by ClientAlive on 2011-06-25
> **donnagarnet said:**
> Thanks, yetiman64.  I tried what you suggested, & got the "Unable to elevate administrative rights" message again.  

Out of curiosity, I used your method to install the "Kindle for PC" app & that worked like a charm (Well, it's on my desktop but I haven't tried it yet).

Is it possible I screwed up something when I first installed Ubuntu (Lucid)?  I've been having massive problems with music players & the eBook viewer as well.

)


What I'm wondering is whether the group you belong to (your user group) has the right permissions to perform the operation.

The second thing I wonder is whether root owns that temp folder or something like that.

It might be wise to check the output of:

```

cd /; ls -la

```

and look for that temp folder listing. See if it has ". . . root:root . . ." in the line or ". . . uname:uname . . ." in it. (Where "uname" is your actual user name, of course).
----------------------

Edit:

I thought I'd heard it said alot that Adobe doesn't play nice with Wine (that Wine doesn't run Adobe products well). Maybe that's changed though.

---

### Post by donnagarnet on 2011-06-27
Entering "sudo chmod +x/setup.ex" into a terminal as Vansch76 suggested resulted in a message that "no such file or package exists".

Entering 
cd /; ls -la
into a terminal resulted in "user name username".

BTW, the "KindleforPC" app doesn't do anything but sit on my desktop.

You've all been so patient & I appreciate it.  Thanks.

---

### Post by yetiman64 on 2011-06-27
You need to cd to the directory that setup.exe is in before running the chmod command, your terminal defaults to your home directory and if your download directory is different you will get that error.

Edit: you may find it easier to just use the nautilus window and open the folder setup.exe is in, right click setup.exe and then select properties then the permissions tab and tick the box at the bottom. That is the graphical means of doing that chmod command.

---

### Post by ClientAlive on 2011-06-27
> **donnagarnet said:**
> 
Entering 
cd /; ls -la
into a terminal resulted in "user name username".

. . . you've all been so patient & I appreciate it.  Thanks.


I think that last statement applies to you too donnagarnet. Linux can be a beast sometimes. Lol.

Btw, is that a typo in your statement about the files ownership, or is it really representative of how it looks - with a space between words in the first part and no space in the part after the colon (the groupname).

I'm not sure it would have any effect if there were a difference between the uname and groupname; and, if there were, I'm sure it would also have to do with whether it was just set up that way intentionally. Maybe someone else knows better, maybe just a typo anyway. Just offering my observation at this point.

Thanks

---

### Post by donnagarnet on 2011-06-29
That gap was a typo.  Sorry about that.

Am I correct in assuming that my Home Folder is Nautilus?  If so, then I did go into that folder to fiddle with setup.exe.

I am considering starting over from scratch to see if that solves the problems I've been having with WINE & media players.  Running the Windows restore discs to wipe out everything, then re-installing Ubuntu.

I like Linux.  It's been easier to learn than I anticipated, & I don't miss the freezes & crashes associated with WinBlows.  I certainly don't miss the frequent notices: "IE is shutting down for no reason.  Wait while someone at Microsoft pretends to care."

---

### Post by ClientAlive on 2011-07-01
> **donnagarnet said:**
> 
Am I correct in assuming that my Home Folder is Nautilus?  If so, then I did go into that folder to fiddle with setup.exe.


What happened Donna? Did everyone just leave you? Well, it is the 4th of July weekend.

Nautilus is the name of the file browser, installed by default, in Ubuntu (and probably a lot of other Linux Distros too). It could be compared to Windows Explorer (not Internet Explorer, Windows Explorer).

So actually, from the top, it goes root; which is designated by the forward slash "/" (without the quotes of course). Then, after that (or, one of the files inside it) is "home". Then, inside "home" you will find 'your' home directory. It will be named whatever you chose for a user name when you installed. (There are ways of renaming it but I doubt you have done that). If more user accounts are added they will also be in "home" and so, with additional user accounts, you would see more than one folder in there and each one would be named whatever their user name is.

So, you can see that folder from the command line by typing:

```

cd /home; ls

```

or by typing

```

ls /home

```

The first one is actually two commands strung together and they are conencted to each other by the semicolon at the end of the first one. In 'that' code it is first navigating you to "/home" and then, the second command, displaying the contents of that folder (or "directory" is a synonym). The second one is just one command and it is not moving you anywhere but is just displaying the contents of "/home". For it, "ls" is the command and "/home" is where you are telling it to look. If you were to just type "ls" it would display the contents of wherever you are located (the directory/ folder you are in).

There's one other thing that some people have a tough time getting their mind wrapped around (I sure did) . . .

In Linux, when you enter the terminal, you do not start out at root "/". Where you start out at is in your home directory, which is actually a subdirectory (to use Window talk) of root. So where you start out at is inside "/home/username" (username being whatever yours is). It's very subtle, but notice there is a difference between "/home" and "/home/username". The second one is actually inside 'your' home directory.

There is an excellent free eBook available called "The Linux Command Line" by William Shotts. It takes a hands on approach and has you follow along with the book as you go. It is very easy to understand and covers all the basics. If you choose to dwell on what he's teaching you a little; and, if you even go as far as to try experimenting with some of the principles, and taking them a step further, it's unbelievable how much you can learn - and fast too.

That book can be found here: [http://www.linuxcommand.org/tlcl.php](http://www.linuxcommand.org/tlcl.php)

Then there's this, which I just found. It's really cool: [http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)


> **donnagarnet said:**
> 
I am considering starting over from scratch to see if that solves the problems I've been having with WINE & media players.  Running the Windows restore discs to wipe out everything, then re-installing Ubuntu.


If that is the route you choose (and I hope you don't cause it's probably overkill) there is a much easier way to do it. You can simply install Ubuntu again, right over the top. The idom us geeky people use is "paving over". Part of the install process of Ubuntu will format the drive and formatting it will wipe everything out, completely. Then it will install right on top of it. No need to add the Window's step in between. Make certain you have any personal data you want to keep backed up first though.

:)

> **donnagarnet said:**
> 
I like Linux.  It's been easier to learn than I anticipated, & I don't miss the freezes & crashes associated with WinBlows.  I certainly don't miss the frequent notices: "IE is shutting down for no reason.  Wait while someone at Microsoft pretends to care."

I'm glad you like it. I started using it about 3.5 mos ago and I absolutely love it! There are a lot of really good reason's to roll with Linux; and, if you stick around I'm sure you'll hear them. Granted some people can almost make a political thing out of it, but the facts are still the facts. The security is much better, There is an amazing lack of viruses (pretty much none, ever). There are some technical reasons behind this. They aren't difficult to understand but I'll let you discover them in your own time - I won't ruin the surprise. It is much more stable. It's free. There's a lot more you can do with it. Granted, there is a learning curve, but there was that with Windows too wasn't there? It's worth the learning curve - I think. AND, if you learn to use the command line, it does even more. The power of the command line is amazing. That may sound funny to read right now, but it's true. Let me give you an example.

I once tried to create over 17 billion (billion, not million) folders at one time using a single line of code. (This was when I was reading that book I mentioned - I was taking it to the next level, lol). Well I didn't realize I was asking the thing to make that many of em' I was learning about something called wildcards (wildcards are awesome!). I made a thread on it, here in these forums; and, one of the guys who responded, did the math and told me something something cubed was equal to some number and that I had tried to make over 17 billion. Of course the computer froze up and crashed. It never did make all those folders but it sure was hilarious  :)

On the command line, you can also do something called piping "|" (that's a pipe). Pipes let you take what one program puts out and run it into another program. A person can pipe several programs together on the command line and get an end result in only one line of code. To do this by clicking you would have to click click click all over the place and still only do one operation at a time. You'd have to run one program and then close it and run the next till you got what you wanted. (There's a "tee" too by the way).

Not everyone is into this kind of thing or not to the same degree as the next person, I get that. I think it's pretty cool though and I hope you get to experience some of the things I have with Linux.

God bless. Hope you have a great weekend. I actually tried to reply two days ago but my finger accidentally bumped some key and it wiped out everything I wrote. It was about as long is this one and I'd spent a while writing it. I was so disgusted it took me till now to get over it and make my way back here. Sorry. :)

ttyl

---

### Post by jtarin on 2011-07-02
> **ClientAlive said:**
> What happened Donna? Did everyone just leave you? Well, it is the 4th of July weekend.
A pork rib in one hand a mouse in the other.:P

---

### Post by ClientAlive on 2011-07-02
> **jtarin said:**
> A pork rib in one hand a mouse in the other.:P


ur killin' me dude!

:)

---

### Post by donnagarnet on 2011-07-09
Sorry I didn't get back to you kids.  

A few days ago, I opened up the software catalog & checked out the "There are six recommendations for you" link.  One of them was Q4WINE, which I installed out of...curiosity, desperation...who knows?

It works.  Well, sometimes.

I've been able to install some of my favorite games, but with varying results.

While it seems random what Q4WINE will & won't install, it seems the older the program, the less likely it is that it will install.  

I have a chess program I like because the computer "player" made occasional snarky comments about bad moves.  The voice is the one feature that doesn't work.

I installed "Virtual Tour of Edinburgh Castle" (I'd live there if the Scottish government would let me).  The narration & maps work, but the video bits won't load.

I started with a new three-game CD I bought.  The game I'd played all the way through on Windows doesn't work (when I try it, it puts my monitor to sleep) but the other two work fine.  

Another game works well except for the full-screen command.

I was able to install one mostly-text quiz game, & it works fine, but a couple of Biblical & Torah study programs won't.  

A few games install, but I can't play them.

When I tried installing Adobe Digital editions, I got the same result as I did with "regular" WINE.

I hope you kids had a great Fourth (or weekend).

---

### Post by ClientAlive on 2011-07-09
> **donnagarnet said:**
> Sorry I didn't get back to you kids.  

A few days ago, I opened up the software catalog & checked out the "There are six recommendations for you" link.  One of them was Q4WINE, which I installed out of...curiosity, desperation...who knows?

It works.  Well, sometimes.

I've been able to install some of my favorite games, but with varying results.

While it seems random what Q4WINE will & won't install, it seems the older the program, the less likely it is that it will install.  

I have a chess program I like because the computer "player" made occasional snarky comments about bad moves.  The voice is the one feature that doesn't work.

I installed "Virtual Tour of Edinburgh Castle" (I'd live there if the Scottish government would let me).  The narration & maps work, but the video bits won't load.

I started with a new three-game CD I bought.  The game I'd played all the way through on Windows doesn't work (when I try it, it puts my monitor to sleep) but the other two work fine.  

Another game works well except for the full-screen command.

I was able to install one mostly-text quiz game, & it works fine, but a couple of Biblical & Torah study programs won't.  

A few games install, but I can't play them.

When I tried installing Adobe Digital editions, I got the same result as I did with "regular" WINE.

I hope you kids had a great Fourth (or weekend).


There's always virtualization. You can install Window in Virtual Box or something . . .

Hope you had a great 4th too Donna.

Peace out ol' girl.;)

---

### Post by donnagarnet on 2011-07-14
Just an update.  Yesterday I reinstalled Ubuntu from a disc "free with magazine".  Today I'm using WINE to install programs & it works!!! I have Adobe Digital editions!!!!

Thanks so much for your help, kids.  You've been terrific!:KS:KS:KS:KS

---

### Post by ClientAlive on 2011-07-15
> **donnagarnet said:**
> Just an update.  Yesterday I reinstalled Ubuntu from a disc "free with magazine".  Today I'm using WINE to install programs & it works!!! I have Adobe Digital editions!!!!

Thanks so much for your help, kids.  You've been terrific!:KS:KS:KS:KS


That's great Donna! Glad to hear it. Can you go in and "Mark this thread as solved" though. Other people see that tag and it let them know if they can find help with their problem. It's under "Thread Tools."

Thanks.

---

