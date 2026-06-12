---
title: "Update Manager &amp; Open Office"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by Archie69 on 2009-04-16
Hello 

I Was hoping someone could help.  I recently re-installed 8.04, and it works fine just a few snags so far.  First off, I get an error when running update manager.  I started to receive it soon after I got an update for my screenlets.  This is the error:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513

I have no idea what that means.  It started when I added third party software in synaptic.  Any ideas?


Lastly, Open Office usually works well for me.  But now that I've re-installed it using the add/remove option (it adds Open Office 2.4) it doesn't have Times New Roman Font.  I don't get it?  Anyone know how to run an update for it or to update it to 3.0?

Thanks

---

### Post by llamabr on 2009-04-16
When adding lines to your synaptic manager, you must also add the keys that go with it, to authenticate.  You only did the first part.

For times, you can add:

msttcorefonts

---

### Post by ranch hand on 2009-04-16
I wouldn't worry too much about the key.  If you log into the launchpad site I think they have a blurb on getting their keys which will end that message.

As for Open Office, I don't know WTF.  I am on an Intrepid install right now but what I have is 2.4 on here.  I think that is what I have on my main OS (Hardy) too.  I certainly have Times on here.

I would go to synaptic and uninstall again.  I would then go to terminal and:
```

sudo apt-get install openoffice.org

```
I think that will straighten it out.

---

### Post by Archie69 on 2009-04-16
I think that might work.  Uninstalling it and re installing it through terminal.  But heres a stupid question...how do I uninstall Open Office?

---

### Post by Archie69 on 2009-04-16
Also, regarding the error message when i run the update manager, I ran 

 sudo gedit /etc/apt/sources.list   in terminal to get the source list, but as I imagined it only made me lost more.  The index page is:

[http://ppa.launchpad.net/](http://ppa.launchpad.net/)

any help is greatly appreciated.
Thanks

---

### Post by ranch hand on 2009-04-17
To uninstall go to synaptic and click on search.

Type in  openoffice.org and hit enter.

Scroll down to openoffice.org.  Anything marked there as installed just right click on it and select mark for uninstall.  When done marking click on the aply applet on the tool bar.

Did you try sudo apt-get install msttcorefonts  as suggested by llamabr?

I am also wondering why you reinstalled in the first place.

---

### Post by Archie69 on 2009-04-17
Thanks.  It seems to be working fine.  Open Office is working well and I have Times again.  I also realized that if your default language is set to English (Canadian) there is no dictionary so it wont pick up your spelling mistakes. 

No to clear up that Update Manager problem.  Thanks

---

