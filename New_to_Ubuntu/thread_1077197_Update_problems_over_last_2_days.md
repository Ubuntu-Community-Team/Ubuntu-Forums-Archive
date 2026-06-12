---
title: "Update problems over last 2 days"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Scunnered on 2009-02-22
I am totally confused and require assistance as the following goes straight over my head and I don't know what to do.

Yesterday I downloaded upgrade packages only to receive an error message which I reported and in reply I was advised the following

&#8220;*** This bug is a duplicate of bug 296219 ***
     [https://bugs.launchpad.net/bugs/296219](https://bugs.launchpad.net/bugs/296219)

** This bug has been marked a duplicate of bug 296219
    package kde-window-manager 4:4.1.2-0ubuntu13 failed to 
install/upgrade: trying to overwrite 
`/usr/share/kde4/apps/kconf_update/plasma-add-shortcut-to-menu.upd', 
which is also in package kdebase-workspace-data&#8221;

Today I was advised of further upgrades and this time I am informed that I can only perform a partial upgrade.  Working on the basis that half a loaf is better than none I accepted this but during the download I received a request for a new password for root user against the heading of &#8220;configuring mysql-server-5.0&#8221;  As I had no idea of what this was or for I clicked on forward and the download after another 2 requests for a password completed.

Can you please advise if this KDE problem will keep causing partial upgrades and if so how do I resolve this.  I am not too concerned about using KDE so if there is a way to remove it in its entirety then please tell me how to do so. 

As to MySql-Server what if anything should I be doing about that request for a password. Is an individual password required and if so what do I do about it.  Again is MySql absolutely necessary? 

Thanking you in anticipation

---

### Post by yeats on 2009-02-22
Okay - I see on the launchpad page you link to that someone has a workaround:

> 
I encountered this problem while trying to run the upgrade from kde 4.1 to 4.2 from Intrepid Ibex listed here:

[http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)

To get around this problem, I was able to run the following command:

sudo dpkg -i --force-overwrite /var/cache/apt/archives/kde-window-manager_4%3a4.2.0-0ubuntu1~intrepid1~ppa7_i386.deb

This pushed through the change, though failed on some other dependencies. But then I was able to successfully run this command:

sudo apt-get dist-upgrade -f

And I'm up and running on kde 4.2. Thanks to Jonathan Thomas for the tip.

before running the "sudo dpkg -i" command you'll probably want to follow that directory path yourself using Nautilus or by doing this in the terminal:

```
cd /var/cache/apt/archives
ls kde-window-manager*
```

this will make sure the name of the .deb package is correct - otherwise, run the "sudo dpkg -i" command in the terminal.  This will force the overwrite that your error message is complaining about.

Regarding MySQL - if you didn't select to install this yourself, that means another program you have selected depends on it to function.  When you set up MySQL initially, it prompts you to pick a root password - just for MySQL, meaning it won't affect any other program.  If you just hit Enter at those prompts, it probably means that your password is "Enter" (the key, not the word ;-) ).

Make sense?

---

### Post by Scunnered on 2009-02-22
chrissharp123

Thank you for your reply. 

Working with the terminal scares the life out of me but I will give this a try !

I bought this laptop pre-installed with 8.10 but had great difficulty in establishing a wireless connection.  Eventually the provider connected to my system and downloaded his set up which seemed to be based on KDE.  Up till then I was happy with Gnome and that was why I asked was KDE required at all.

I will go with the flow as regards MySql and hope for the best.

I have been rather enjoying our national drink so I will defer until tomorrow the changes you suggest and will get back to you.

Once again thanks

---

### Post by ricardisimo on 2009-02-22
I'm having similar install/update issues. Do I enter _MY_ root password? A different one? Am I ever going to be asked for a password on behalf of MySQL again, or is this just for installation?

---

### Post by yeats on 2009-02-22
> Working with the terminal scares the life out of me but I will give this a try !

Taking risks is the only way to learn.  Be careful, pay attention to error messages, and don't panic! :-)

@ricardisimo

> I'm having similar install/update issues. Do I enter MY root password? A different one? Am I ever going to be asked for a password on behalf of MySQL again, or is this just for installation?

You can pick whatever you want - it has nothing to do with ubuntu's root password (which is not available anyway, or shouldn't be :-) ).  You will need it again if you ever need to configure something with MySQL (e.g., adding an account for a program like Drupal or Wordpress).

---

### Post by ricardisimo on 2009-02-22
In other words, this is not some virus scam intent on prying my password out of me? Thank you very much.

---

### Post by yeats on 2009-02-22
> In other words, this is not some virus scam intent on prying my password out of me? Thank you very much.

No, not at all.  MySQL is one of the most widely-used and trusted database management programs out there.  Whatever you enter there is just for your own use.

---

### Post by Scunnered on 2009-02-23
chrissharp123

Thanks for you words of care end encouragement.  Before I go down that road I would advise you that I received an e-mail this morning.

Basic info from it advises "Status in &#8220;kdebase-workspace&#8221; source package in Ubuntu: Fix Released

Bug description:
Binary package hint: kdebase-workspace

Failed update.

ProblemType: Package
Architecture: i386
DistroRelease: Ubuntu 9.04"

Based on this should I still follow the fix or will it be part of the next upgrade?
Although 9.04 is not too far away I had no intention to switch until I had a better grasp on things with the current version. What would you suggest?

Once again many thanks

---

### Post by orethrius on 2009-02-23
Wow, sorry to butt in here uninvited, but Jaunty (9.04) is not even out of the test phase yet.  Stick with Ibex (8.10) until either your provider is willing to support any snags the Jaunty developers might hit, or Jaunty hits the release cycle proper.

---

### Post by ikisham on 2009-02-23
Do you have any usage problems really besides not being able to upgrade kde? Just try to fix it if you want to following chrissharps' suggestion or anything you find at the bug page. Then by april the 23rd we'll get that brand new 9.04 when kde 4 will be much more tested.

---

### Post by Scunnered on 2009-02-23
orethrius & ikisham

What I was wondering was the upgrade going to be issued prior to the new 9.04 version. I am still finding my way with 8.10 and don't want to change versions perhaps until the next LTS issue.

It was a question of should I **apply** the fix or will it be **supplied in the next update?  **

---

### Post by orethrius on 2009-02-23
I think you answered your own question there, but in case you're still wondering...

Yes.  From my perspective, when a fix is available - assuming it's an appropriate solution to the problem - it should be applied.  At this point, it's difficult to tell whether or not 9.04 will have it when it ships.

That is, unless you're still referring to the Partial Upgrade, which is something of a mixed blessing.

---

### Post by ikisham on 2009-02-23
When using 8.10 (I've just switched to 8.04.2) I installed kde, through synaptic I think, to try it. Then it came with 4.1.3 version (I think) and it was somewhat 'crude' so I upgraded to 4.2 (a lot of basic tweakings didn't work in 4.1) by enabling 'Intrepid proposed' updates in System>Administration>Software Sources so it came when I asked for an update. Beware that you may have to filter only the kde updates, I didn't do it and because of that, because I had fiddled with the system trying to install other stuff and so on, I just downgraded to Hardy. Intrepid was working great though, just it had a lot of stuff loaded that I didn't even know. Something to note: in the updates that came trough 'proposed' my sound just boosted from 'less-than-Windows' to 'better-than-Windows' level. Idk if it was the kde package (although the sound got better in Gnome too) or some other stuff, but it was something maybe particular to this machine.
P.S.- thinking better, maybe I've used apt-get install kde.No, no..it was through Add/Remove.. 'KDE 4' :-)

---

### Post by yeats on 2009-02-23
> It was a question of should I apply the fix or will it be supplied in the next update? 

Just so you're not so much in the dark here about what the workaround I highlighted in my first response does . . . The command is:

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/kde-window-manager_4%3a4.2.0-0ubuntu1~intrepid1~ppa7_i386.deb
```

To know what's going on here, you need to understand a little about what a Debian package is.  Basically a .deb package installs software from source code in such a way that all dependencies are installed along with it (or conversely, that no dependencies being used by other programs are changed/removed).  This is the beauty of the Debian system - it keeps your system from breaking every time you install software.  This is why new users are advised to just install from the repositories using the tools provided (Synaptic, apt-get, Adept, etc.) rather than building from source.  I have broken a system myself by unintentionally ripping out the dependencies from several programs with the goal of installing something kind of useless.  This taught me the value of caution (and backups) :-).

Occasionally, especially when working with "unstable" software like say, KDE 4.2 (sounds like that's what you're doing here, right?) that is still being developed for specific systems, you'll run up against problems like yours where the installer finds something wrong and will not continue without your forcing it to.  This is when it helps to have some of this knowledge under your belt.  (That and the willingness to go out on a limb and take calculated risks).  Okay - back to your command :-).  We'll go piece by piece.  

The basic way to install a .deb package that you download from the Internet is this:


```
sudo dpkg -i *package-name*.deb
```

dpkg (type "man dpkg" for details in the _man_ual) is the Debian installer program.  The "-i" flag means "install."  You run this as root ("sudo"), and follow the command with the name of the package you're installing ("*package-name*.deb").  You then get feedback about the success/failure of the command.  The "--force-overwrite" option (see the man page) should be self-explanatory since the installer is complaining about an overwrite issue.  If you're running this command while in a directory other than where the .deb package is located (type "pwd" to "print working directory" - shows where you are in the directory tree), you have to specify the directory path, hence:
```

/var/cache/apt/archives/kde-window-manager_4%3a4.2.0-0ubuntu1~intrepid1~ppa7_i386.deb
```

(which, by the way _cannot_ be the actual package name - the "%" symbol is not valid - this is why I advised listing the filename to see what it's actually called)

Does that help clear things up about what's going on here?  My short answer would be - do the workaround.  You'll continue to get error messages about broken or half-installed packages until you do.

Oh - and you might want to get some basic command line skills - they really do pay off!  I used to be fearful myself, but it's all about learning new things, right? :-)

---

### Post by Scunnered on 2009-02-23
chrissharp123

I will follow your advice and see what happens with the workaround. I hope that this will resolve the problems.

As to command line skills I agree that learning is the thing but so far I have been unable to where I can learn this skill.  Would this be covered in the Bash Shell section of the Begining Ubuntu Linux Book?

I have seen posts where instruction has been given to amend a file but having a look at the example there are times when I just am unable to get my head round what is being asked.  This is where I struggle.

I will give things a go and get back to everyone.

Thanks again

---

### Post by yeats on 2009-02-23
> **Scunnered said:**
> chrissharp123

I will follow your advice and see what happens with the workaround. I hope that this will resolve the problems.

As to command line skills I agree that learning is the thing but so far I have been unable to where I can learn this skill.  Would this be covered in the Bash Shell section of the Begining Ubuntu Linux Book?

I have seen posts where instruction has been given to amend a file but having a look at the example there are times when I just am unable to get my head round what is being asked.  This is where I struggle.

I will give things a go and get back to everyone.

Thanks again

Happy to help.  If you're okay learning from books, there are several that outline the basics.  One I've got is Learning the Bash Shell from O'Reilly (Google books version here: [http://books.google.com/books?id=YLSw9FCL37sC]("http://books.google.com/books?id=YLSw9FCL37sC")).  Another book that I have found to be extremely helpful is How Linux Works ([http://books.google.com/books?id=wOGUuoHUyAEC]("http://books.google.com/books?id=wOGUuoHUyAEC"))

Otherwise, just start basic.  Learn to navigate around the shell - it's the best way to get started.

Good luck.

---

### Post by alexcckll on 2009-02-23
Personally, I'd suggest you take one step further back into the arms of fully-supported apps.

Forget downloading software from anywhere out on the Net.  Instead - stick to Synaptic, and only pull from the Ubuntu repos.

ANYTHING else - raise an enhancement request (I believe Ubuntu term would be a New App bug?), tell the release management team where to find the app...

And wait.

It should be in the repositories eventually... and you'll be able to select it within Synaptic, knowing it'll run happily, as supported apps.

Out of interest - re Upstream issues - surely we end-users report our incidents on Launchpad and let more experienced people liaise with upstream?

---

### Post by yeats on 2009-02-23
> Personally, I'd suggest you take one step further back into the arms of fully-supported apps.

Forget downloading software from anywhere out on the Net. Instead - stick to Synaptic, and only pull from the Ubuntu repos.

I think this is good general advice for true newbies, though everyone will reach the point, either out of curiosity or necessity, where they will want to branch out from "repository only" software.  I think people just need to take the time to educate themselves about what's going on before they venture beyond the safety of the repos. :-)

---

### Post by Scunnered on 2009-02-24
**chrissharp123**

I followed your instruction and as far as I can see everything worked OK. As there are no Updates available to check further I trust that everything will work when the next once comes around. 

Looking further in the book that I bought I see a section Introducing the Bash Shell and I will see what this does for me.  If I struggle there I will see if any of the books you refer to are available in my Library although I doubt it very much.

I dont think that I will be attempting to use Linux professionally at my age, one of the reasons of switching was to keep my mind active but looks to be a road too far.


**alexcckll**

I take your suggestion that as a first step I should stick with Synaptic and feel that it will meet my needs.

My sincere thanks to all for your kind assistance

---

### Post by ricardisimo on 2009-02-25
Something's definitely not entirely right about the system on both of my comps. Clearly, the folks at KDE have been busy, as I have received update notices thrice in the past two weeks or so. However, every time there is a new batch of KDE updates, Update Manager suggests a Partial Distribution Upgrade, and as I am on 8.10, this is of course nonsense.

Furthermore, all of the KDE packages are categorized as Backports, and that doesn't seem right. When I tried to update them via Synaptic, I got a strong warning about installing software that cannot be authenticated and malicious individuals prowling about the web. Then I ran "sudo aptitude update", and suddenly that warning is gone, but all of the KDE apps are still from Backports.

Does none of this strike anyone as odd? Is no one else having these issues?

---

### Post by Scunnered on 2009-02-26
I am happy to report that today's update had some kde items and this time I was able to properly download this time without being offered a partial update.

Once again my sincere thanks to all who assisted me in resolving this problem

---

