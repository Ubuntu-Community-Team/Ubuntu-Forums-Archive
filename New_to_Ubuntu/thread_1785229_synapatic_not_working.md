---
title: "synapatic not working"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by Whitsboy on 2011-06-18
When I try to install through synaptic I receive this dialog box....

This has happened after an update. Can anyone give me some clues as to what has happened. Thanks

---

### Post by Whitsboy on 2011-06-18
Sorry my screen print of the dialog box did not work. This is what the dialog box said...
"E: Malformed line 62 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."
Thanks

---

### Post by Rubi1200 on 2011-06-18
Hi,

please post the output of this command:

```
cat /etc/apt/sources.list
```

---

### Post by Whitsboy on 2011-06-18
When I try to use synaptic package manager I receive an error message
[B][I]"E: Malformed line 62 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."[/I][/B]

This has happened after an update.

Does anyone have any ideas what has happened & how to fix it? Thanks

---

### Post by DeMus on 2011-06-18
> **Whitsboy said:**
> When I try to use synaptic package manager I receive an error message
[B][I]"E: Malformed line 62 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."[/I][/B]

This has happened after an update.

Does anyone have any ideas what has happened & how to fix it? Thanks

Okay, open a terminal. In there type:
gedit /etc/apt/sources.list

Now a simple text-editor will open. At the bottom-right you see a line counter: ln 1
Go down to line 62 and see what it says there. Compare the syntax of this line to lines above and beneath it.
Press ctrl-a (meaning press the ctrl-key and while keeping it pressed you press a) and then in the same way ctrl-c. Answer this message here and press ctrl-v. Now we can have a look at your file to see what is wrong.

When you receive the answer from the forum you have to open the same text file again but now like this:
sudo gedit /etc/apt/sources.list
You will be asked for your password. Type it and remember you won't see it appear on screen. Just type it and press enter.
Watch out: you are now the computer administrator and can ruin a lot in the computer. So please just do what has been told here.

---

### Post by Whitsboy on 2011-06-18
```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb apps
deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb apps
deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) maverick meerkat
deb-src [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) maverick meerkat
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick free non-free
deb deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick free non-free
```

---

### Post by DeMus on 2011-06-18
Okay I see what is wrong:

Open a terminal again, type:

sudo gedit /etc/apt/sources.list
Type your password and enter.

Now in the text editor go to line 62, last line of the file.
At the start of the line it says:
deb deb-src

This should be deb-src

Remove the first deb and save the file. Close gedit and the terminal.
Now it will work again.

Success.

---

### Post by MrEgg on 2011-06-18
Here is what you do :


1. [ALT]+[F2]
2. Type in : gksudo gedit /etc/apt/sources.list
3. enter your password

4. Once opened, go down to the end of the list.
The very last line starts with "deb deb". Remove the first "deb "

5. The 3rd line from bottom says :
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
Remove that line entirely.

6. Restart Synaptics. Click the Reload button.

Let us know how this goes.

Egg

---

### Post by uRock on 2011-06-18
Duplicate threads merged. Please do not create multiple threads on the same topic.

Regards,
uRock

---

### Post by wildmanne39 on 2011-06-18
Hi, if the other methods fail, try this.
```
sudo rm -r /var/lib/apt/lists/* -vf
```
The rm -r command needs to be entered exactly as shown here, If you enter the wrong package to remove you could wipe out your whole system.
```
sudo apt-get update && sudo apt-get upgrade
```
These two commands will update the source list and then upgrade your packages.

---

### Post by uRock on 2011-06-18
> **wildmanne39 said:**
> ```
sudo rm -r /var/lib/apt/lists/* -vf
```
[s]This command looks dangerous. Can you explain its use and give warnings as to what it will do if entered incorrectly?[/s] Thanks for adding the line of advice. 8)

---

### Post by crispy_420 on 2011-06-18
> **uRock said:**
> This command looks dangerous.

You think? Looks like every file (*) in that directory (/var/lib/apt/lists/) gets recursively (-r) removed (rm) by force (-f) verbosely (-v).


[http://ss64.com/bash/rm.html](http://ss64.com/bash/rm.html)

Better get it right the first time... Lets see how it works in a VM.

---

### Post by crispy_420 on 2011-06-18
Yeah just got done running in a VM and lets just say it was wise of me to back up first.

The initial command wiped that directory like I thought. To see the impact I opened synaptic and it did not error out. So I reloaded to get this attached error as attached.

Then running the second commands got me this error:

```
E: Lists directory /var/lib/apt/lists/partial is missing.

```

So maybe just removing that extra deb at the start of the last line is your best bet. Now off to recover my VM.

---

### Post by wildmanne39 on 2011-06-18
> **crispy_420 said:**
> Yeah just got done running in a VM and lets just say it was wise of me to back up first.

The initial command wiped that directory like I thought. To see the impact I opened synaptic and it did not error out. So I reloaded to get this attached error as attached.

Then running the second commands got me this error:

```
E: Lists directory /var/lib/apt/lists/partial is missing.

```

So maybe just removing that extra deb at the start of the last line is your best bet. Now off to recover my VM.Hi, thats because you did not finish with the second command that is on the previous page.
```
sudo apt-get update && sudo apt-get upgrade
```I talked with Urock about it, if the command in its current form was harmful it would have been removed, people all over the forum has used that command followed by the second command to fix there update problems, look on the previous page and you will see the other command that followed that one. I see you said you run the second command, is that right? if so did you check your synaptic updates before you began to make sure it did not have an error, because like I said this as been used many times, I am not the one that started using it, it is used by ubuntu members as well.

---

### Post by Whitsboy on 2011-06-18
All's good, Thank you Mr Egg & DeMus. I do apologise uRock for the duplicate threads.

---

### Post by crispy_420 on 2011-06-18
I repeated the steps and got the same issues with synaptic and command line update/upgrade this morning. The process is flawed in that current state but if you issue a separate command after the fact 'sudo mkdir -p /var/lib/apt/lists/partial
' as directed here: [http://ubuntuforums.org/showthread.php?t=648198](http://ubuntuforums.org/showthread.php?t=648198) it resolves the issue but lists every package as "new" to the repos. And no offense to the original poster but isn't doing a rm as root unusually risky? If he/she copied or transcribed the syntax wrong it could wipe something else for good.

I'm not trying to argue or anything, but trying those commands twice got the same result.

---

### Post by wildmanne39 on 2011-06-18
> **crispy_420 said:**
> I repeated the steps and got the same issues with synaptic and command line update/upgrade this morning. The process is flawed in that current state but if you issue a separate command after the fact 'sudo mkdir -p /var/lib/apt/lists/partial
' as directed here: [http://ubuntuforums.org/showthread.php?t=648198](http://ubuntuforums.org/showthread.php?t=648198) it resolves the issue but lists every package as "new" to the repos. And no offense to the original poster but isn't doing a rm as root unusually risky? If he/she copied or transcribed the syntax wrong it could wipe something else for good.

I'm not trying to argue or anything, but trying those commands twice got the same result.Hi, I am sorry that it did not work on your system, I know you are an experienced user and I respect your opinion, I tried that command on my production system because I had faith that it works and I checked my synaptic and update manager before I did the command and it worked, I did not have any trouble. Yes if some one totally changed the file to be fixed they could do a lot of damage, then the update command it downloads the list again and anything in the old file causing problems will be gone. The problem with the partial list is because when then update && upgrade command was run for some reason the upgrade did not complete. Again, I am sorry for your trouble, I started using this set of commands after seeing several problems with the update manager fixed using those commands. Do you have another set of commands that will o the same thing?
I thought maybe these command will.
sudo apt-get update
to update your package list.
Then 
Code:
sudo apt-get autoclean
to clean up any partial packages.
Then 
Code:
sudo apt-get clean
to clean up the apt cache.
Code:
sudo apt-get autoremove
will clean up any unneeded dependencies.

Will these commands do the same thing as it looks like it will?

---

### Post by crispy_420 on 2011-06-18
All he needed was that extra deb removed and it worked for him. So us debating this is a non-issue for the purpose of his/her initial post.

---

