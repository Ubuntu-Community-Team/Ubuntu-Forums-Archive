---
title: "impossible to add creative common extension to OO"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by al.adab on 2009-04-29
hello

please see the screenshot in attachment. I'm trying to add the file "ccooo.oxt" ([http://wiki.creativecommons.org/OpenOfficeOrg_Addin](http://wiki.creativecommons.org/OpenOfficeOrg_Addin)) and I get the error at the screenshot. 

Any idea? Shall I post this at the OO.org forum instead?

Thanks.

---

### Post by Didius Falco on 2009-04-29
I took a look at the link you posted, and followed it to here:

[http://extensions.services.openoffice.org/project/ccooo](http://extensions.services.openoffice.org/project/ccooo)

Once there, I skimmed through the comments and found this:

> Tue, 06/24/2008 - 21:34 — splaestro

       One has to have a Java Runtime Engine selected for use within OO for the extension to install properly. Go into Tools -> Options and under the OpenOffice.org section look for
Java.  Even if it lists a JRE there, make sure it's selected and then try again.
 Thanks to Nathan Yergler for the answer on this one.



I make no promises - I haven't tried using this extension. That said, I think it's worth a try.

I hope this helps...

---

### Post by al.adab on 2009-05-01
Thanks Didius Falco for taking the time to find this. I checked and JRE is enabled in OO.org writer. Tried to disable it, close writer, open writer and enable it again. Still the creative commons ext doesn't install...

---

### Post by Didius Falco on 2009-05-01
Are you trying to install it directly from the download (the **Open With** choices list) or from a saved location, like your desktop?

I just downloaded it to my desktop and it installed with no problem.

---

### Post by Didius Falco on 2009-05-01
Having read a little bit about that error, it looks like the problem could be with java, not that particular extension.

You may want to check out your java install. I'd open Synaptic and see what java engine(s) you have installed. Maybe uninstall and then reinstall your java and see if that helps.

Sorry I can't be more help - I'm just throwing out ideas I'd try, I'm certainly no expert.

Approaching OO and maybe even Java might help. Their error messages are certainly non-helpful to finding a resolution.

Good luck, and sorry I couldn't be more help...

---

### Post by al.adab on 2009-05-02
That's all right, it looks like I've got the latest Java package installed. I tried to re-install it, but it made no difference. I'm wondering if it might help to re-install OO.org - I seem to recall a similar situation in the past but can't remember what exactly I did to uninstall + reinstall OO.org...any suggestion?

---

### Post by Didius Falco on 2009-05-02
Open Synaptic, do a search for **openoffice** (all one string) and mark** openoffice.org** for complete removal. After it finishes, select it again and install.

---

### Post by jmszr on 2009-05-02
al.adab,

You need to install (through Synaptic Package Manager is how I did it) openoffice.org-java-common. That should do it.

---

### Post by Didius Falco on 2009-05-02
DING DING DING!!! I think we have a winner!

---

### Post by al.adab on 2009-05-02
Tried this as well after doing a fresh installation of OO.org. Now the Java error no longer appears, but it's not clear if the extension has been installed - for some reason Creative Commons doesn't appear under "insert" as indicated at [http://wiki.creativecommons.org/OpenOfficeOrg_Addin](http://wiki.creativecommons.org/OpenOfficeOrg_Addin)

---

### Post by jmszr on 2009-05-02
al.adab,

I don't know exactly why it finally appeared under insert for me just now - I opened and closed all my openoffice apps and restarted my computer - ran updates in OOo extension manager - there was no update for ccooo.oxt but somewhere along the line it showed up under insert. So I don't really have any advice for you other than that's what I was doing when it showed up. I'm thinking the update (even though there wasn't one) might have done it. *shrug*

---

### Post by al.adab on 2009-05-04
Also here it appeared after re-starting the computer. Don't know the reason either but at least it's there now :)

---

