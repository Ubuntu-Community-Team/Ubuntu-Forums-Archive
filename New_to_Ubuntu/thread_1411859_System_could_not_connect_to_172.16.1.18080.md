---
title: "System could not connect to 172.16.1.1:8080"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by naata on 2010-02-20
Hei, I'm new on linux. This morning i installed karmic koala. I tried browsing using firefox, and it works. Then i want to update ubuntu by update manager. but i always got error. here the message:
[INDENT]W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to 172.16.1.1:8080 (172.16.1.1), connection timed out

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-id.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-id.bz2)  Unable to connect to 172.16.1.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-id.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-id.bz2)  Unable to connect to 172.16.1.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-id.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-id.bz2)  Unable to connect to 172.16.1.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-id.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-id.bz2)  Unable to connect to 172.16.1.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Unable to connect to 172.16.1.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-id.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-id.bz2)  Unable to connect to 172.16.1.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-id.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-id.bz2)  Unable to connect to 172.16.1.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-id.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-id.bz2)  Unable to connect to 172.16.1.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-id.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-id.bz2)  Unable to connect to 172.16.1.1 8080:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg](http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to 172.16.1.1:8080 (172.16.1.1), connection timed out

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-id.bz2](http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-id.bz2)  Unable to connect to 172.16.1.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Unable to connect to 172.16.1.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-id.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-id.bz2)  Unable to connect to 172.16.1.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-id.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-id.bz2)  Unable to connect to 172.16.1.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-id.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-id.bz2)  Unable to connect to 172.16.1.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-id.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-id.bz2)  Unable to connect to 172.16.1.1 8080:

W: Some index files failed to download, they have been ignored, or old ones used instead.
[/INDENT]I tried to change the server, when i choose "select best server", then i got message : 
[LEFT][INDENT]No suitable download server was found
Please check your Internet connection.

[/INDENT][LEFT]Is there any help for this?
[/LEFT]
[/LEFT]

---

### Post by cariboo on 2010-02-20
I would suggest trying a different server. Go to System->Administration->Software Sources, then click the download from drop down and select other, then click the Find the best server button. Let the program find the best server for you.

---

### Post by naata on 2010-02-21
i've been tried that. please read last part of the post.

---

### Post by gmargo on 2010-02-22
> **naata said:**
> Could not connect to 172.16.1.1:8080 (172.16.1.1)

It looks like you have configured a network proxy, but the proxy software is not running.  Firefox works because it has it's own proxy settings, separate from the Gnome desktop settings, which is what the update manager will use (I think.)

On the Gnome desktop, go to System->Preferences->Network Proxy.  Is it configured for "Direct internet connection" or "Manual proxy configuration"?  If Manual, try Direct.  If already Direct.... Not sure...

---

### Post by naata on 2010-02-22
i have tried both. "no proxy" and "manual proxy" using 172.16.1.1. still doesn't work. :(

---

### Post by gmargo on 2010-02-22
Random thoughts:

Is your IP address in the 172.16.1.X range? (Use **ifconfig** command to see IP address.)

Was this a fresh install or an upgrade?  (Could be a leftover)

Do you have any environment variables like *http_proxy* with this address? (Use **env** command to see environment variables.)

Do you have a proxy configured in the /etc/apt directory?  (grep for 8080 with **cd /etc/apt **; **grep 8080 * */***)

What tool are you using to update?  If it is **synaptic**, synaptic has it's own proxy configuration in it's preferences.  

Run **aptitude update** at the command line, which will remove Gnome from the equation.

If none of that works, I'd be grepping all over the place for that 8080.

---

