---
title: "Installing GDebi on Remix"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by captaincalculus on 2009-04-25
Hi, I'm returning to Linux after several years.  I just installed Ubuntu Netbook remix on my MSI Wind.

Since wireless works right out of the box, it's worth trying out.

I absolutely require flash player with Firefox and tried installing.  When I got stuck I looked at [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) and tried to follow it.  This site suggests using Gdebi package installer as a Firefox helper.  Gdebi doesn't appear to be installed.

I located and downloaded Gdebi, but have no clue how to install it.

TIA

---

### Post by cariboo on 2009-04-26
TO install the gdebi package manually open an Applications-->Accessories-->Terminal and type:

```
sudo dpkg -i gdebi
```

It may be a lot easier using Add/Remove Programs or Synaptic Package manager to install it, as installing it manually, doesn't install the dependencies.

---

### Post by 3rdalbum on 2009-04-26
Why didn't you do:

```
sudo apt-get install gdebi
```

Having said that, I believe Gdebi should be installed already.

---

### Post by 3rdalbum on 2009-04-26
Why didn't you do:

```
sudo apt-get install gdebi
```

Having said that, I believe Gdebi should be installed already.

---

### Post by captaincalculus on 2009-04-26
Thanks.  Turns out GDebi was installed.  I still don't know how to use GDebi as a Firefox helper, but I did get Flash installed.

Took a bit for me to discover that I needed to save the .deb file and then use the file browser to go to the desktop.  When I clicked on the file, the option to use GDebi on it was right there.

I'm very impressed with Remix.  I hadn't used Linux in several years.

---

### Post by billgoldberg on 2009-04-26
> **captaincalculus said:**
> Thanks.  Turns out GDebi was installed.  I still don't know how to use GDebi as a Firefox helper, but I did get Flash installed.

Took a bit for me to discover that I needed to save the .deb file and then use the file browser to go to the desktop.  When I clicked on the file, the option to use GDebi on it was right there.

I'm very impressed with Remix.  I hadn't used Linux in several years.

Just saying that it would be better to use the repository to install stuff, instead of downloading apps from the web.

You can use the cli app: apt-get or aptitude, or use Add/Remove (applications -> add/remove) or synaptic package manager (system -> administrations -> synaptic package manager).

---

### Post by anjilslaire on 2009-04-26
Yes, doing
```

sudo apt-get install ubuntu-restricted-extras

```

would have gotten you flash along with lots of other cool bits as well.

---

