---
title: "Unable to configure file sharing, administrator interface seems to be on the blink"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by NickyTheTickyDestroyer on 2007-03-25
Hi I'll freely admit i am a noob. Have only been using Linux for a few months

I want either
[LIST=1]
[*]A method of changing folder permisions to allow sharing from konsole
[*]Or someone to tell me whats possibly causing this problem and how to fix it
[/LIST]


My problem is that when i try to set the file permissions to allow file sharing over a network i cant actually get the administrator privileges to run.

I.e. I right click on the file or folder in konqueror then go to the properties menu, 

then to the share tab, 

then press configure file sharing

then enter administrative password.

And thats where it all goes tits up the menu that loads up just isn't useable, it's almost as if it's still locked out.

[ATTACH]28263[/ATTACH]

The screenshot is from trying to access the same menu from the system setting menu's sharing section but essentially the same thing happens.

I have looked around on the forum and tried googling for file sharing problems in Kubuntu edgy but have had no joy.

I used Dapper before edgy and have only recently swapped over (full install from dvd not an upgrade) but know it worked fine before.

Has anyone out there every heard of this before???:confused:

---

### Post by NickyTheTickyDestroyer on 2007-03-26
OK problem solved

was simple (as I expected it might be), just didn't have samba actually installed. Easy enough to fix by just using Synaptic or Adept and adding samba.

Found the solution on the Kubuntu specific forum

Doh

also found some useful stuff on sorting out permissions between windows machines and Linux using Kcontrol.

[http://kubuntuforums.net/forums/index.php?topic=3080936.0]("http://kubuntuforums.net/forums/index.php?topic=3080936.0")

Scroll down and keep and eye on the posts by ebtech

---

### Post by 9a3eedi on 2007-04-10
Hmm.. I had the same problem.. with Kubuntu Edgy. So I tried doing this, but Adept doesnt let me get the Samba package, telling me that it's going to break other packages or something

in apt-get, these are the messages I get..

```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.22-1ubuntu4) but 3.0.22-1ubuntu4.1 is to be installed
E: Broken packages


```

Seems that this issue will be solved with time, once the ubuntu people sort this out.. hmm?

is there any way to get an older package that wont conflict with the samba-commons package?

---

### Post by NickyTheTickyDestroyer on 2007-04-16
I installed the samba files using synaptic which you can choose to install using adept

i am using Kubuntu Edgy as well so i know it can be achieved even if it is kinda messy to use 2 different package managers

---

