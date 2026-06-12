---
title: "Auto Typer"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by Hosmion on 2009-09-06
Hello everyone.. I had searched the forums for a good auto typer for something, like a video game, or anything else for that matter...

I don't want to have to type in a long list of codes..  Is there a download able light-weight, or small apt-get install (name) program for auto typing?

---

### Post by Lukica18 on 2009-09-06
Hey there.

Although i never needed a auto typer (aka macro) software for linux, i found out that xmacro is good choice.
To install it open your synaptic package manager and search for xmacro.

here is a link for usage

[http://ikester.blogspot.com/2007/01/im-huge-fan-of-autohotkey.html](http://ikester.blogspot.com/2007/01/im-huge-fan-of-autohotkey.html)

---

### Post by makariolewis on 2009-09-06
Autokey is another famous "auto typer."
[http://autokey.sourceforge.net/](http://autokey.sourceforge.net/)

They have an Ubuntu PPA, which is a software channel. That means that you can install software without typing in "long lists of code," although you do have to do a few minor things in order to add the channel. There are instructions on the PPA page:
[https://launchpad.net/~cdekter/+archive/ppa](https://launchpad.net/~cdekter/+archive/ppa)

---

### Post by Hosmion on 2009-09-06
How do I download AutoKey?

Do I need a special program to extract it to the correct place, and it says I need to open it with "Archive Manager"

---

### Post by Lukica18 on 2009-09-06
Use the second link that [makariolewis]("http://ubuntuforums.org/member.php?u=907500") has provided.
It contains instructions ;)

---

### Post by Hosmion on 2009-09-06
I do not see Instructions.

---

### Post by ks07 on 2009-09-06
> **Hosmion said:**
> I do not see Instructions.
They are at the top of that page, in the box entitled "**Description**".

Here are the instructions from the site:
[QUOTE=AutoKey PPA]This PPA contains the latest debs of AutoKey for Ubuntu. To install AutoKey, you must first enable the PPA on your system:
1. Open Software Sources (System->Administration->Software Sources)
2. Navigate to the "Third Party Sources" tab.
3. Click "Add"
4. Enter the APT line below that corresponds to your Ubuntu version that starts with "deb".
5. Click "Add Source"
6. Click "Close"
7. It will prompt you to reload your software cache. Click "Reload".
8. Now install the package "autokey" from Synaptic, or using the command below:
sudo apt-get install autokey
[/QUOTE]

---

### Post by Hosmion on 2009-09-06
I'm Jaunty 9.04 Jackalope..  What do I do for the deb thing?

---

### Post by Lukica18 on 2009-09-06
Scroll a bit down on that page.
You'll see something like this
> Install packages:                            Copy the lines below and add them to your system's software                  sources. ([Read about installing]("https://launchpad.net/+help/soyuz/ppa-sources-list.html"))
                                 Display sources.list entries for:  Karmic (9.10) Jaunty (9.04) Intrepid (8.10) Hardy (8.04)         
        deb [http://ppa.launchpad.net/cdekter/ppa/ubuntu](http://ppa.launchpad.net/cdekter/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/cdekter/ppa/ubuntu](http://ppa.launchpad.net/cdekter/ppa/ubuntu) jaunty main 

Just add both of them i guess

---

### Post by makariolewis on 2009-09-06
1. Go to System > Administration > Software Sources, and click on the Third Party tab.
2. Go to this link: [https://launchpad.net/~cdekter/+archive/ppa](https://launchpad.net/~cdekter/+archive/ppa). On that page, scroll down to where it says "Install Packages." Make sure Jaunty (9.04) is in the dropdown box. Copy the first line that is there. It starts with **deb** and ends with **main**.
3. Back in Software Sources, click "Add.." and paste that line (beginning with deb and ending with main) and click "Add Source." Then go back to the website, copy the line beneath the line you just pasted (beginning with **deb-src** this time) and do the same thing.
4. Close Software Sources, and hit reload when prompted.

---

### Post by Hosmion on 2009-09-06
> **makariolewis said:**
> 1. Go to System > Administration > Software Sources, and click on the Third Party tab.
2. Go to this link: [https://launchpad.net/~cdekter/+archive/ppa]("https://launchpad.net/%7Ecdekter/+archive/ppa"). On that page, scroll down to where it says "Install Packages." Make sure Jaunty (9.04) is in the dropdown box. Copy the first line that is there. It starts with **deb** and ends with **main**.
3. Back in Software Sources, click "Add.." and paste that line (beginning with deb and ending with main) and click "Add Source." Then go back to the website, copy the line beneath the line you just pasted (beginning with **deb-src** this time) and do the same thing.
4. Close Software Sources, and hit reload when prompted.

I did it three times, the two individually, and the two together..  But, I got an error...

What should I do?

---

### Post by Hosmion on 2009-09-06
Bump

---

### Post by cariboo on 2009-09-06
What error do you get? Could you paste it in your next post?

---

### Post by Hosmion on 2009-09-06
Just using the first one alone :

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BCD80C6A6E3C0CE5

Just using the second one alone :

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BCD80C6A6E3C0CE5

Using them both together, highlighted, then pasted, no revision :

(Too long, will not go..  But there is definitely an error)

---

### Post by Lukica18 on 2009-09-06
try to enter this into terminal and repeat the steps mentioned above

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys [1024R/6E3C0CE5]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0x4022579E8E3015F1466460BDBCD80C6A6E3C0CE5&op=index")

and after that

sudo apt-get update 

everything is on that site. Just learn to read all of the stuff

---

### Post by makariolewis on 2009-09-06
[Lukica18]("http://ubuntuforums.org/member.php?u=904837") is right. Everything is on the website. His key instructions should work for you.

If you're curious about what that error is, it basically means that the third party channel that you added is unverified, and Ubuntu is not sure if it's a trustworthy site. If you look on the PPA site, it has a signing key. By adding this key, Ubuntu knows that the PPA you added is legit.

---

