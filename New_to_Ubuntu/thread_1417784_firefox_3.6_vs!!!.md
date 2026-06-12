---
title: "firefox 3.6 vs!!!"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by mbele3000 on 2010-02-27
I just updated firefox 3.5 to firefox 3.6 and I dont want it half of my extensions that I really need are not compatible with it how do I downgrade? I got the tar.gz file and have followed some online tutorials but with no success help please and thank you

---

### Post by mkvnmtr on 2010-02-27
I run 3.6 from the Ubuntuxilla repository on one system and I have found no extentions that do not work. On another system I run the development repository for I think 3.6.7pre. On that one indeed there are some that do not work.Which are you running? Maybe you need to change sources.

---

### Post by Merk42 on 2010-02-27
As mkvmtr said what are the extensions? Pretty crappy developers if they couldn't update to 3.6 compatibility.

If you are dead set on downgrading to 3.5, it would help to know how you got 3.6 in the first place.

---

### Post by Martin Marshalek on 2010-02-27
I just did this a few minutes ago actually, though not for the same reason. Assuming you did it the right way and updated using the Mozilla Stable PPA, it should be a very simple process. Open up the terminal and paste:
```
sudo apt-get autoremove --purge firefox
```

Then open up a root file browser and delete the firefox 3.6 folder in /usr/lib/.

Remove the Mozilla Stable PPA and go into synaptic and install firefox, firefox-gnome-support, firefox-3.5-gnome-support (or something like that).

---

### Post by lovinglinux on 2010-02-27
> **Martin Marshalek said:**
> Then open up a root file browser and delete the firefox 3.6 folder in /usr/lib/.


Deleting such folder manually is not recommended. I don't know why you needed to do that. Let the package manager take care of this.

@mbele3000

You can run several extensions that are not updated by overriding compatibility. The are a couple of methods of doing that, but I recommend using the [Add-on Compatibility Reporter](https://addons.mozilla.org/en-US/firefox/addon/15003), since it also allows to report if the extension works with the new version of Firefox or not. Additionally, don't forget to update your extensions to get the latest compatibility patches.

If you really want to downgrade, then depends how you installed Firefox 3.6 in the first place. If you are using a ppa, then disable it and re-install the firefox packages. If you are using Ubuntuzilla, simply uninstall it. If you have just extracted a downloaded tar file from Mozilla, then simple delete the extracted folder and delete /usr/local/bin/firefox if you have one.

See the [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) for more info.

---

### Post by -kg- on 2010-02-27
> **mbele3000 said:**
> I just updated firefox 3.5 to firefox 3.6 and I dont want it half of my extensions that I really need are not compatible with it how do I downgrade? [COLOR="Red"]I got the tar.gz file[/COLOR] and have followed some online tutorials but with no success help please and thank you

How did you install 3.6?  From a .tar file?  If so, I don't think the above instructions will work since you will not have used a repository.  If you have installed Firefox 3.6 from a .tar file, then [this site]("http://www.tuxfiles.org/linuxhelp/softinstall.html") has some good instructions on removing it (as well as installing .tar files).

---

### Post by sports fan Matt on 2010-02-27
Just have a question...Is there any difference between this extension (Add-on Compatibility Reporter) and Nightly tester tools?  I ask cause I'd think NTT could force extensions to work.

---

### Post by lovinglinux on 2010-02-27
> **sox fan Matt said:**
> Just have a question...Is there any difference between this extension (Add-on Compatibility Reporter) and Nightly tester tools?  I ask cause I'd think NTT could force extensions to work.

There are differences, but I don't remember exactly, since I stopped using NTT a while back. As far as I remember they use different methods for disabling the compatibility check. While the Add-on Compatibility Reporter changes the compatibility check of all extensions, the NTT seems to change something on each extension. I have found complicated to revert the changes of NTT unless I uninstalled it.

I like the Add-on Compatibility Reporter because it integrates with add-on manager, allows to report if the extension works after disabling the compatibility check and is made by Mozilla.

---

### Post by mbele3000 on 2010-02-27
The one extention that I really loved was firetorrent and that no longer works with FF 3.6. There were 2 others as well that did not cross over either. But all I want to do is kill 3.6 and reinstall 3.5 its funny some things in Ubuntu ARE NOT EASY as they should be and this is one of em. Please I really just want to uninstall 3.6 and reinstall 3.5 thats all!

---

### Post by lovinglinux on 2010-02-27
> **mbele3000 said:**
> Please I really just want to uninstall 3.6 and reinstall 3.5 thats all!

See my first post. It would help if you could tell how you installed Firefox 3.6 in the first, as already mentioned on other posts, because the removal method depends on how you did the upgrade.

---

### Post by mbele3000 on 2010-02-28
Yea I can even go back with repositories!??!?! Any one .....
OKAY well I said it from the beginning 
 No one can answer the question.... 

 How do I uninstall firefox 3.6 and install firefox 3.5 

  It updated via the update in the package manager (i.e. firefox)  so that was that and well I want to go back....

 Why is that so hard to answer.........

---

### Post by lovinglinux on 2010-02-28
> **mbele3000 said:**
> Yea I can even go back with repositories!??!?! Any one .....
OKAY well I said it from the beginning 
 No one can answer the question.... 

 How do I uninstall firefox 3.6 and install firefox 3.5 

  It updated via the update in the package manager (i.e. firefox)  so that was that and well I want to go back....

 Why is that so hard to answer.........

Seriously? Have you read my first post?

With that attitude you won't get much support, at least from me. Good luck.

---

### Post by mbele3000 on 2010-02-28
1st please do not confuse my frustration with a "bad attitude" lighten up!
2nd I did follow your guide and the other ones posted and they DID NOT WORK! I am stuck with Namoroka firefox.

---

### Post by lovinglinux on 2010-03-01
> **mbele3000 said:**
> 1st please do not confuse my frustration with a "bad attitude" lighten up!
2nd I did follow your guide and the other ones posted and they DID NOT WORK! I am stuck with Namoroka firefox.

OK. Perhaps I misunderstood you, since English is not my first language.

Could you please tell which ppa you have enabled?

---

### Post by mbele3000 on 2010-03-01
Ok I'm glad you asked that thank you very much BTW(by the way).
 For some reason I have 2 it seems.
 
ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu
ppa.launchpad.net/mozillateam/firefox-stable/ubuntu

---

### Post by lovinglinux on 2010-03-01
> **mbele3000 said:**
> Ok I'm glad you asked that thank you very much BTW(by the way).
 For some reason I have 2 it seems.
 
ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu
ppa.launchpad.net/mozillateam/firefox-stable/ubuntu

Disable both, then run this:

```
sudo apt-get purge firefox && sudo apt-get install firefox
```

This should restore Firefox to 3.5.

---

