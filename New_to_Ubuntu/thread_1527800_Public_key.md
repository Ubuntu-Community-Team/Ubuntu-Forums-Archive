---
title: "Public key"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by Vege 4wd on 2010-07-09
Hi I tried using update manager this morning and got this error:
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 
followed by a serires of numbers.

Any way I can resovle the problem?

---

### Post by barney385 on 2010-07-09
> **Vege 4wd said:**
> Hi I tried using update manager this morning and got this error:
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 
followed by a serires of numbers.

Any way I can resovle the problem?

I posted a similar thread 3 hours ago and I haven't found a fix yet.

I'm going to start looking elsewhere and will post back if I find anything.

---

### Post by barney385 on 2010-07-09
I've been trying this in terminal:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com  313D312748A22A95; gpg --export --armor 313D312748A22A95 | sudo apt-key  add -

Of course, you have to use your own key error in place of the key I'm using.

This is the prescribed way to fix this problem as far as I can tell, yet it won't work for me.

Your guess is as good as mine on this one.

Still searching.

---

### Post by oldos2er on 2010-07-09
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` where KEYID is the "series of numbers".

---

### Post by Vege 4wd on 2010-07-09
Hi I tried the code and got this error:

W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release: The following signatures were invalid: BADSIG 54422A4B98AB5139 Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>

thanks for the replies.

---

### Post by Vege 4wd on 2010-07-10
Just bumping.

---

### Post by Vege 4wd on 2010-07-10
Hi after a google this code worked for me: 

sudo rm -f /var/lib/apt/lists/partial/*

---

### Post by Vege 4wd on 2010-07-10
Hi I am back again as I thought it was fixed however when I try and update and view the files individually I see it has "hit" and "failed" but nothing downloads?????

all help would be apprieciated.

---

### Post by d3v1150m471c on 2010-07-10
this is why i use 9.10

---

### Post by mcduck on 2010-07-10
> **oldos2er said:**
> ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` where KEYID is the "series of numbers".

That won't work, since that repository is on virtualbox.org servers, not on ubuntu's servers.

Just follow the instructions they have on the Virtualbox site for adding the repository and importing the GPG key:

```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -

```
[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

---

### Post by Vege 4wd on 2010-07-10
Hi, I just cant seem to work it out. I found a link to the "key" a huge block of letters and numbers but as much as tried I could not work out what to do with it.

---

### Post by mcduck on 2010-07-10
> **Vege 4wd said:**
> Hi, I just cant seem to work it out. I found a link to the "key" a huge block of letters and numbers but as much as tried I could not work out what to do with it.

Just run the command from my post, it will download and import the key for you.

Or, since you have already downlaoded the key manually, you can open a terminal in the directory where you have downloaded the key and execute this command:
```
sudo apt-key add oracle_vbox.asc

```

---

### Post by Vege 4wd on 2010-07-10
Hi mcduck. The code from previous post did not work. 
This is the output from the last code:

aaron@aaron-laptop:~$ sudo apt-key add oracle_vbox.asc
gpg: can't open `oracle_vbox.asc': No such file or directory

When I clicked the link to the key it came up with a long list of characters but I do not think anything downloaded. 

Apprecieate the help.

---

### Post by oldos2er on 2010-07-10
> **mcduck said:**
> That won't work, since that repository is on virtualbox.org servers, not on ubuntu's servers.


Oops. Thanks Mcduck.

---

### Post by mcduck on 2010-07-11
> **Vege 4wd said:**
> Hi mcduck. The code from previous post did not work. 
This is the output from the last code:

aaron@aaron-laptop:~$ sudo apt-key add oracle_vbox.asc
gpg: can't open `oracle_vbox.asc': No such file or directory

When I clicked the link to the key it came up with a long list of characters but I do not think anything downloaded. 

Apprecieate the help.

OK, so you didn't actually download the key file, you just opened it.

In that case use the command from the previous post, the one that starts with "wget...". That will download *and* import the key for you.

---

### Post by k3lt01 on 2010-07-11
Go back to the page that you found the key on and highlight the key, now paste it into a text file in gedit. Save that file with a name that suits the repository you are trying to use. 

Now go into Software Sources, System > Administration > Software Sources. Go to the Authentication tab, click on the Import Key File find the key you saved before and import it. Click Close let it refresh and your done.

---

### Post by Vege 4wd on 2010-07-11
All working now thanks heaps.

---

