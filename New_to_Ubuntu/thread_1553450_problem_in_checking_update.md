---
title: "problem in checking update?"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by munna.cheyur on 2010-08-15
each and every time while checking update in "update manager" following error message coming pls anyone help me to solve this problem. (i have attached a screen shot image of that report) thank u for in advance.

---

### Post by Paqman on 2010-08-15
What it's saying is that it's having trouble with a PPA that you've added. Delete the PPA from your software sources, go to the Launchpad page for that PPA and set it up again.

---

### Post by howefield on 2010-08-15
This thread might be of interest to you.

[http://forum.videolan.org/viewtopic.php?f=13&t=70719](http://forum.videolan.org/viewtopic.php?f=13&t=70719)

---

### Post by inameiname on 2010-08-15
You actually have two issues:

1. The GPG error is merely a missing GPG key. They accompany all sources in your sources.list as a security thing. You can add it by copying and pasting this into the terminal:

"gpg --keyserver keyserver.ubuntu.com --recv &#65279;5A16033A9A6FE242
gpg --export --armor &#65279;5A16033A9A6FE242 | sudo apt-key add - && sudo apt-get update" - without the quotes.

It'll ask for your password at start, so just enter it, and run it all. That's all. Then the key will be added.

2. This is unrelated to the GPG key, as the PPA, c-korn, requires another key (71346C834013082) , which you already have since it's not asking for this one as well. So no worries about that. And why it says it Failed to Fetch the Packages.gz means from their source, [http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386](http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386), it is currently not there. Sometimes that happens, as they are either fixing something, removed it, or something. If it becomes a bothersome, simply remove the PPA from the sources.list and you'll be good.

---

