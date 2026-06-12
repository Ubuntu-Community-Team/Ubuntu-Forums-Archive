---
title: "An Error Occured."
date: 2009-09-30
forum: New to Ubuntu
---

### Post by suomalainen on 2009-09-30
Ubunteros,

I keep getting the following error message listed below when I run the "Update Manager". How can I resolve this issue? What do I need to do?

Also, I removed Opera but as seen below it still looks like something is still sought for?

I also get this message too:


Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".


What do I need to do to get rid of these error messages and the "lightbulb" that keeps popping up each time I start up my PC?

Thank you!!!!



W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by suomalainen on 2009-09-30
n

---

### Post by pieisgood4589 on 2009-09-30
Please edit your original post before double-posting.

The bug for your second error was submitted, and the fix can be found here~
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24234](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24234)

---

### Post by suomalainen on 2009-09-30
All,

I reinstalled OPERA and now when I run the UPDATE MANAGER I get the following message:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061


Regarding the Apt Authentication issue, I ran the command below but don't know how to tell if that helps anything.

sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update


What needs to be done?

---

### Post by suomalainen on 2009-09-30
F.Y.I.

According to:

[http://www.webopedia.com/TERM/D/double_post.html](http://www.webopedia.com/TERM/D/double_post.html)

I did NOT double post.

In online forums double posting is when a user posts the same message or slightly edited versions of the message more than once, in more than one discussion thread. Double-post is also called cross-post.

---

### Post by QIII on 2009-09-30
As long as you don't double dip...

If you look at the page at the URL in the following:

W: GPG error: [http://deb.opera.com]("http://deb.opera.com/") stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

it gives you some tips for adding the key both in Debian and Ubuntu.

As for the other, I'll have to dig.

---

### Post by dearingj on 2009-09-30
You can fix the launchpad.net error by entering this command in the terminal (I just found this by doing some digging around help.launchpad.net):

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 60D11217247D1CFF

---

### Post by suomalainen on 2009-09-30
QIII & dearingj,

Thank you very much for pointing me in the right direction. Because of your help and assistance on the above issue(s) I was able to resolve the matter. The latter being based upon not receiving any error messages once "Update manager" was run.

Thank You for your help and support.!

---

