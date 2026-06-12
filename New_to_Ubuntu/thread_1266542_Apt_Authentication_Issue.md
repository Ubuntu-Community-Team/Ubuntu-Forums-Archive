---
title: "Apt Authentication Issue"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by ericstrom on 2009-09-14
I keep getting an App Authentication warning when updates run. What is this and how do I correct it ? When I investigate further, here's the message I get ....

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 04A38A9C1B826E04
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

W: Failed to fetch [http://deb.opera.com/opera/dists/sid/Release](http://deb.opera.com/opera/dists/sid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

So what in the world do I do to fix this ? ANy help you can provide would be appreciated.

---

### Post by 73ckn797 on 2009-09-14
You need to locate for the signature key, as stated in the error message, that is missing.

---

### Post by ericstrom on 2009-09-14
Sorry, still learning. 

What do locate for the signature key mean ? How do I do that ?

---

### Post by DasEi on 2009-09-14
Both, Launchpad and Opera have a pgp-key to verify your downloads won't get corrupted. googled for you "ubuntu opera repo key", found 

[http://www.google.de/url?q=http://deb.opera.com/&ei=bdKuSo3OEoWnsAad0K3ZDA&sa=X&oi=spellmeleon_result&resnum=1&ct=result&usg=AFQjCNHv9YKD-A6I5F4BJ3f6TWOCJg-FRw](http://www.google.de/url?q=http://deb.opera.com/&ei=bdKuSo3OEoWnsAad0K3ZDA&sa=X&oi=spellmeleon_result&resnum=1&ct=result&usg=AFQjCNHv9YKD-A6I5F4BJ3f6TWOCJg-FRw)


anything you need is explained there, do same for launchpad

greetz, DasEi

---

### Post by nhasian on 2009-09-14
adding authentication keys for each repository was a pain in the butt.  I'm glad that the process is automated now in Ubuntu Karmic Koala.  You just add the repository and it automatically grabs the key.

---

### Post by Toadinator on 2009-09-14
> **nhasian said:**
> adding authentication keys for each repository was a pain in the butt.  I'm glad that the process is automated now in Ubuntu Karmic Koala.  You just add the repository and it automatically grabs the key.

really? thats awesome! citation, maybe?

---

### Post by drs305 on 2009-09-14
The new *Karmic* command for adding PPA repositories is:
```

sudo add-apt-repository ppa:<repo>
```
where <repo> is the name of the Launchpad PPA.
Example:
sudo add-apt-repository ppa:nhander
Not only will it add the repository to the /etc/apt/sources.list.d folder, it will automatically import the public key.

There is no man page as yet.

For previous editions:
For any missing public key message, you can run the following to import the key:
```

gpg --keyserver keyserver.ubuntu.com --recv-keys [COLOR="DarkRed"]<key>[/COLOR] && gpg --export --armor [COLOR="DarkRed"]<key>[/COLOR] | sudo apt-key add - 

```
You can input the entire alphanumeric code or just the last 8 characters. You can also combine multiple keys in a single set of commands, as in:
```

gpg --keyserver keyserver.ubuntu.com --recv-keys 9D1A0061 1B826E04 && gpg --export --armor 9D1A0061 1B826E04 | sudo apt-key add - 

```
The server appears to be down at the moment, but this set of commands will work once it's back up.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by 73ckn797 on 2009-09-14
> **nhasian said:**
> adding authentication keys for each repository was a pain in the butt.  I'm glad that the process is automated now in Ubuntu Karmic Koala.  You just add the repository and it automatically grabs the key.

+1
That is good to hear.

---

### Post by 73ckn797 on 2009-09-14
> **ericstrom said:**
> Sorry, still learning. 

What do locate for the signature key mean ? How do I do that ?

My bad. Grammatical error: "You need to locate the key" is what I meant. It is no longer a concern due to the responses from others.

---

### Post by ericstrom on 2009-10-19
A continuation of this problem. I followed the advice here and used this :

gpg --keyserver keyserver.ubuntu.com --recv-keys 9D1A0061 1B826E04 && gpg --export --armor 9D1A0061 1B826E04 | sudo apt-key add -

No more app authentication error. But my system no longer alerts me to updates. I have to force an update by using update manager

How do I get to getting auto updates

---

### Post by drs305 on 2009-10-19
> **ericstrom said:**
> A continuation of this problem. I followed the advice here and used this :

gpg --keyserver keyserver.ubuntu.com --recv-keys 9D1A0061 1B826E04 && gpg --export --armor 9D1A0061 1B826E04 | sudo apt-key add -

No more app authentication error. But my system no longer alerts me to updates. I have to force an update by using update manager

How do I get to getting auto updates

Depending on the version you are running, updates are done on a weekly basis, except for security updates, which are offered immediately.

You can check your update preferences in Synaptic: Settings, Repositories, Updates and see what you have enabled and how often to check. At a minimum, enable Security updates.

---

### Post by ericstrom on 2009-10-19
drs, first, I wanted to say thanks for the code that stopped the app authentication issue. Never mentioned that in my previous posting.

For the settings in Synaptic, I have it set to update daily with auto security. So I'm wondering why it's not giving me the pop up say I have updates waiting. I know I do because I see them when I do a manual update. 

Any other thoughts would be greatly appreciated.

---

### Post by ericstrom on 2009-10-19
drs, first, I wanted to say thanks for the code that stopped the app authentication issue. Never mentioned that in my previous posting.

For the settings in Synaptic, I have it set to update daily with auto security. So I'm wondering why it's not giving me the pop up say I have updates waiting. I know I do because I see them when I do a manual update. 

Any other thoughts would be greatly appreciated.

---

### Post by drs305 on 2009-10-19
I know there have been reported problems of a similar nature regarding Update Manager. Which release are you using?

I'm going over to Launchpad to search the bugs list, but it would help to know the release you are using. If I find something I'll update this post.

---

### Post by ericstrom on 2009-10-20
Using Jaunty 9.04

Any thoughts or ideas ? Thanks in advance for the continued support

---

### Post by drs305 on 2009-10-20
When does Update Manager say it updated last?

Do you get any error messages if you run
```
sudo apt-get update
sudo apt-get upgrade
```

Have you tried changing servers?

Have you had any problems with your sources.list?

One thing that has worked for some is replacing their sources.list. You can generate a new one from here:

[http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/")

Make a copy of your old one. If UM starts working again, you could try restoring your original one to see if the problem has gone away.

---

