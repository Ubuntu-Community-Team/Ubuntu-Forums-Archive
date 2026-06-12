---
title: "Installing Banshee"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by disx on 2009-05-01
so i just installed ubuntu today. i've never used any linux system before. i'm trying to install banshee and i ran into this problem when i tried to add the apt line (deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) intrepid main) to the Third Party tab:


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7


here's the link to where i was following instructions:

[https://edge.launchpad.net/~banshee-team/+archive/ppa](https://edge.launchpad.net/~banshee-team/+archive/ppa)

any ideas?

thanks!

---

### Post by Didius Falco on 2009-05-01
You have to add the Open GPG key to Software sources.

Here is an extract from a link on that PPA explaining how to do it:

> **Step 1:** Visit the PPA's overview page in Launchpad. Let's go back to the [AWN Testing team's PPA]("https://launchpad.net/%7Eawn-testing/+archive") that we were looking at earlier. 
**Step 2:** Click the key fingerprint on the overview page. It'll look something like this: B0BE17C2A0C914F086B7B8327D2C7A23BF810CD5`. 
**Step 3:** This will take you to the key's page in the Ubuntu keyserver. Click the ID, which looks something like this: BF810CD5 
**Step 4:** Copy the public key, which will be something like: -- i.e. the portion starting: 

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXS1/wEEALis4to4JdgrkdRunmSTfB2tYRq99Cdcgdh9up4HzAf1yTZU1EtmETPP1Uy2
vnAFf/cCunL5VRywNJB3QOxiHdvNlijbdsa0H/fT/ulq+A4iDljUEfsaJug+dAB5uEJE0BzZ
agRjgLbFvRYtsKf3BwZizbo4XtWSAm3JSjZCGZKTABEBAAG0IkxhdW5jaHBhZCBQUEEgZm9y
IEF3biBUZXN0aW5nIFRlYW2IRgQQEQIABgUCSXqnWgAKCRBBf7ZCSCH+JPZMAJ4xW7gbpuA+
yedehvDQWdJHHUgseQCgy6NOmAyXqRKrIXWERkXw6h9TsRuItgQTAQIAIAUCSXS1/wIbAwYL
CQgHAwIEFQIIAwQWAgMBAh4BAheAAAoJEH0seiO/gQzVpSID/0FXxTSLtxPHrT7IE9eif5qJ
vjOjzcmOCXe9/3G0ctV8IfYHx0VynddjxgTqJ9WuEjMLVHRgXvK1Rw1XMlik+MeyyHrr9EWQ
DUFbUs+Yc2usRyZY8pVe2Uwy2x7lFsi6VBfo0k9jVsu1l1qBU9BhANJDUTHjR15aPYiUJiZa
13CZ
=a6Gh
-----END PGP PUBLIC KEY BLOCK-----**Step 5:** Paste the public key into a text editor and save it. 
**Step 6:** Open *System->Administration->Software Sources* and click the *Authentication* tab. 
**Step 7:** Click *Import Key File*, select the key you saved earlier and you're done! If you go back to that web page and look just below the box with the "deb" info, you'll see a link to the OpenPGP key. Follow the above steps and you will be able to download from that repository.

I hope this helps...

---

### Post by Elfy on 2009-05-01
You will find on the page you linked to in the apt sources.list entries section details of how to add the key to your system.

In a terminal

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6E80C6B7
sudo apt-get update
```

After the apt update you should have no error. 

Any time that you use a ppa you will need to do the same thing again.

---

