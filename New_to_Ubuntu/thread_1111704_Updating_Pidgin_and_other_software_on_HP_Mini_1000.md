---
title: "Updating Pidgin and other software on HP Mini 1000 MIE"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by chud67 on 2009-03-30
Please forgive the simple question, but I am new to Ubuntu.  I recently bought one of the HP Mini 1000 MIE's with Ubuntu.  I use Pidgin to chat on ICQ.  Recently it stopped working because it needs to be updated.  I get: 
 "The client version you are using is too old.  Please upgrade at http://pidgin.im/" 

 I do update the system periodically through Update Manager, but apparently that doesn't cover Pidgin.  How do I update it?  I'm used to rpm-based distros, so this is new to me.  Thanks in advance for your patience.

---

### Post by dmaxel on 2009-03-30
Since it's part of the distro package found in Add/Remove, it should update over Update Manager....at least that's what I think.

---

### Post by chud67 on 2009-03-30
> **dmaxel said:**
> Since it's part of the distro package found in Add/Remove, it should update over Update Manager....at least that's what I think.

 Yeah, that's what I thought.  It ain't workin' out for me though... :(

---

### Post by chud67 on 2009-03-31
*bump* 

):P

---

### Post by chud67 on 2009-03-31
Ok let me phrase my question in a more general way:  how do you update an individual package in Ubuntu?  Do you first have to point to a repository of some sort?  

 Thanks in advance.

---

### Post by qamelian on 2009-03-31
> **chud67 said:**
> Ok let me phrase my question in a more general way:  how do you update an individual package in Ubuntu?  Do you first have to point to a repository of some sort?  

 Thanks in advance.
You should be able to find a newer release that corrects the problem at:
[http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

Just remember to uninstall the version you currently have before installing the packages from Getdeb. Also, be aware that you might need to uninstall any packages you install from Getdeb before you try to upgrade to the next version of Ubuntu.

---

### Post by i_TheDevil_i on 2009-03-31
well, if u take a look at [http://pidgin.im/download/ubuntu/](http://pidgin.im/download/ubuntu/) it actually tells u what exactly to do to update your pidgin.
> Ubuntu ships Pidgin but does not update it after a release (except for security issues). For those users who desire new releases of Pidgin, we have packaged Pidgin in a PPA. If you encounter problems with these packages, try building from source and report the bug.

To setup the PPA, copy-and-paste these commands into a terminal:
  sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \
      67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
  . /etc/lsb-release
  echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \
      $DISTRIB_CODENAME main | \
      sudo tee /etc/apt/sources.list.d/pidgin-ppa.list

Once this PPA is setup, Pidgin updates will show up in Update Manager along with the usual Ubuntu updates. The PPA will need to be re-setup only after upgrading Ubuntu.

(C) Pidgin.im

hope this helps =)

---

### Post by qamelian on 2009-03-31
> **i_TheDevil_i said:**
> well, if u take a look at [http://pidgin.im/download/ubuntu/](http://pidgin.im/download/ubuntu/) it actually tells u what exactly to do to update your pidgin.

(C) Pidgin.im

hope this helps =)
Actually, this is arguably preferable to my suggestion. Wish I'd thought of it!
:)

---

### Post by chud67 on 2009-04-03
> **i_TheDevil_i said:**
> Ubuntu ships Pidgin but does not update it after a release (except for security issues).

 Ok, I can understand that, but let me ask you this...why does it stop working?  I should at least have the option to carry on using the old version if I want to, you can do that with most applications.  Does Pidgin "break" every time a new version is released?  If so then that sucks, and I'd rather use another IM client.

> The client version you are using is too old. Please upgrade at [http://pidgin.im/](http://pidgin.im/)

---

### Post by chud67 on 2009-04-03
One more question, how do I keep Pidgin from launching at startup? 
In the RedHat world I would use chkconfig to turn it off.  I'm still new to the Ubuntu/Debian world though.  Thanks.

---

### Post by qamelian on 2009-04-03
> **chud67 said:**
> Ok, I can understand that, but let me ask you this...why does it stop working?  I should at least have the option to carry on using the old version if I want to, you can do that with most applications.  Does Pidgin "break" every time a new version is released?  If so then that sucks, and I'd rather use another IM client.
The problem is not the software but the provider of the IM service. When MSN or ICQ or Yahoo change the way their protocol works, any clients that connect to those protocols may break until til they are updated. The same thing happens with the native clients. You can't just install any old version of ICQ and expect it to work. Pidgin only breaks when one of the IM providers changes their protocol.

---

### Post by chud67 on 2009-04-03
> **qamelian said:**
> The problem is not the software but the provider of the IM service. When MSN or ICQ or Yahoo change the way their protocol works, any clients that connect to those protocols may break until til they are updated. The same thing happens with the native clients. You can't just install any old version of ICQ and expect it to work. Pidgin only breaks when one of the IM providers changes their protocol.

That makes some sense, however when I used to use Matt's ICQ (Micq) on my SuSE box, I used it reliably for a couple of years without ever updating it.  I had Pidgin on a new netbook for less than two months and it's already kaput...

---

### Post by MPTony T on 2009-04-03
> **chud67 said:**
> One more question, how do I keep Pidgin from launching at startup? 
In the RedHat world I would use chkconfig to turn it off.  I'm still new to the Ubuntu/Debian world though.  Thanks.

You should be able to go to Preferences>Sessions and uncheck the Pigin box and click save. You can hit ctrl+atl+bkspc to reset and check to see if it worked after you remove it from sessions.

---

### Post by chud67 on 2009-04-03
> **MPTony T said:**
> You should be able to go to Preferences>Sessions and uncheck the Pigin box and click save. You can hit ctrl+atl+bkspc to reset and check to see if it worked after you remove it from sessions.

 MPTonyT, thanks man.  
For all the HP Mini 1000 MIE users, in HP's desktop you would click Settings - Advanced tab - Sessions.

---

### Post by qamelian on 2009-04-03
> **chud67 said:**
> That makes some sense, however when I used to use Matt's ICQ (Micq) on my SuSE box, I used it reliably for a couple of years without ever updating it.  I had Pidgin on a new netbook for less than two months and it's already kaput...
It depends on when the protocols get updated. I remember a few years back when a lot of ICQ users on Windows got annoyed when a protocol update forced them to update to a newer, and some felt inferior, version of the native Windows ICQ app. So, this can even affect the original clients, not just third-party apps like Pidgin. The same thing has happened at least once with MSN and Yahoo.

---

### Post by chud67 on 2009-04-03
Understood.  
I will say this though, I used to love Micq (Matt's ICQ), but I don't think you can find it anymore.  Apparently the original developer died, and the homepage is now gone.  Also there was a feud between another Micq developer and a Debian developer.  
 Micq was really nice though, you could chat on ICQ inside a terminal window.  I liked it a lot better than the bloated GUI chat clients.

---

### Post by chud67 on 2009-04-03
> **i_TheDevil_i said:**
> well, if u take a look at [http://pidgin.im/download/ubuntu/](http://pidgin.im/download/ubuntu/) it actually tells u what exactly to do to update your pidgin.

> 
Ubuntu ships Pidgin but does not update it after a release (except for security issues). For those users who desire new releases of Pidgin, we have packaged Pidgin in a PPA. If you encounter problems with these packages, try building from source and report the bug. To setup the PPA, copy-and-paste these commands into a terminal: 

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \ 67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8 
. /etc/lsb-release 
echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \ $DISTRIB_CODENAME main | \ sudo tee /etc/apt/sources.list.d/pidgin-ppa.list 

Once this PPA is setup, Pidgin updates will show up in Update Manager along with the usual Ubuntu updates. The PPA will need to be re-setup only after upgrading Ubuntu. 

(C) Pidgin.im

hope this helps =)

 That worked for me, after a bit of tweaking.  After running those commands I had to manually edit the /etc/apt/sources.list.d/pidgin-ppa.list file that it created, and add the word "hardy" just before "main", near the end of the line.  Apparently I had to do this because $DISTRIB_CODENAME has no value, for example when you run:  
 
```

cat /etc/lsb-release 

``` 

 it returns several things, but nothing for $DISTRIB_CODENAME.  So I had to add "hardy" to the file, which is basically what the HP Mini 1000 MIE runs (although they call it something else). 

 Anyway I ran update manager and Pidgin updated successfully.  I am now back on ICQ.

---

### Post by mdsmedia on 2009-04-03
Glad you got that sorted out.

It's strange that ICQ didn't work on Pidgin after such a short time.

Did Pidgin come pre-installed on you computer? It may not have been installed from the repositories in the first place, may have been an older version, and Ubuntu wasn't updating it as it usually would.

---

### Post by chud67 on 2009-04-03
Yes, it came pre-installed on my HP Mini.

---

### Post by stchman on 2009-04-03
> **chud67 said:**
> Please forgive the simple question, but I am new to Ubuntu.  I recently bought one of the HP Mini 1000 MIE's with Ubuntu.  I use Pidgin to chat on ICQ.  Recently it stopped working because it needs to be updated.  I get: 
 "The client version you are using is too old.  Please upgrade at http://pidgin.im/" 

 I do update the system periodically through Update Manager, but apparently that doesn't cover Pidgin.  How do I update it?  I'm used to rpm-based distros, so this is new to me.  Thanks in advance for your patience.

You can get the latest pidgin at getdeb.net

[http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

---

### Post by chud67 on 2009-04-16
> **chud67 said:**
> That worked for me, after a bit of tweaking.  After running those commands I had to manually edit the /etc/apt/sources.list.d/pidgin-ppa.list file that it created, and add the word "hardy" just before "main", near the end of the line.  Apparently I had to do this because $DISTRIB_CODENAME has no value, for example when you run:  
 
```

cat /etc/lsb-release 

``` 

 it returns several things, but nothing for $DISTRIB_CODENAME.  So I had to add "hardy" to the file, which is basically what the HP Mini 1000 MIE runs (although they call it something else). 

 Anyway I ran update manager and Pidgin updated successfully.  I am now back on ICQ.

 Just wanted to update everyone in case any HP Mini users do a search and find this thread.  I had to remove the 
 /etc/apt/sources.list.d/pidgin-ppa.list 
file because it was breaking my system's automatic updates through Update Manager. 
 I did make a backup copy of the file in my home directory before deleting it.  That way in case I ever need to update Pidgin manually again I can just put the file back.  
 Hope this helps someone.

---

