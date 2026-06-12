---
title: "Firefox reverting"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by BobJam on 2010-10-19
I want to revert to what was for me the last stable version of Firefox.

I currently have version 3.6.10, and it was an upgrade from the canonical repository on 3.6.8 (I think).

The reason I want to revert is the classic "memory leak" issue, where FF seems to become less responsive as time goes on.  I have no idea if it's actually a "memory leak" issue with FF, **or if such an animal even exists** . . . but I know the symptom I have is that it becomes less responsive as time goes on and slows down the entire system.

I really don't think I need to look at add ons, mainly because I had the same ones with the stable version (3.6.8) and they didn't cause any problem with that version.  And I really don't want to fuss with a "clean" profile.  I haven't looked at the processes, and don't really feel a need to.  Nor do I think it's an issue of too many tabs open, because again I had as many open with the stable version (3.6.8) and they didn't cause any problem with that version.  Rather then troubleshoot 3.6.10, I just want to get back to a version that was stable for me.

So, I want to revert.

I did that some time ago, but now I can't remember the method.

It seems like it would be pretty simple . . . just remove the current version and then install the desired version from the mozilla FTP site.  I don't see a .deb on there for the version that I want to revert to, so I'm guessing I'll have to extract the tar file (with the tar command) to my ~/.mozilla folder . . . or would that be somewhere else . . . like in the /usr/<something> folder?

But I'm thinking there's a few things I should attend to first, before impulsively jumping into this.

Like back up my profile and bookmarks, which I've done.

But I'm confused about removing the current version with the Synaptic Package Manager GUI.  There seem to be a gazillion Firefox entries there (the checked boxes of course), from Firefox to Firefox-3.0-branding (described as "dummy upgrade package for firefox-3-0-> firefox-3.5") to firefox-3.0 (which shows the "Installed Version" as "3.6.10-build1+nobinonly-Oubuntu0.9.10.1") and then "firefox-branding" for "Installed Version" 3.6.10-build1+nobinonly-Oubuntu0.9.10.1.

Some of these will show marked for dependencies, and I'm OK with that, but others don't show up marked at all for dependencies, and I'm wondering what to remove.

My current plan is to save the contents of my ~/.mozilla folder (leaving an empty ~/.mozilla folder) somewhere else and then use it to replace the profile, along with the profiles.ini file.  I have a vague memory that this is what I did before.

I've looked at the mozilla KB on this topic, and I've gotten a little bit out of it, but not enough to feel confident.

So, I'm looking for some "DON'Ts" and some "DO's" and a more precise outline than the general idea I have in my mind.  I'm definitely not sure of myself, and some of what my foggy memory recalls could be wayyyyy off.

Anyone?

---

### Post by BobJam on 2010-10-19
Bump

---

### Post by ratcheer on 2010-10-19
Firefox 3.6.11 is either available or becoming so, soon. Maybe they have fixed the bug.

Tim

---

### Post by BobJam on 2010-10-19
Is that going to be in the Canonical repository, or are you talking about strictly a download from Mozilla instead?

---

### Post by beew on 2010-10-20
> **BobJam said:**
> Is that going to be in the Canonical repository, or are you talking about strictly a download from Mozilla instead?

Open Synaptic, go to Settings > Repositories. Then choose the tab "Other Software" and add the line
> ppa:ubuntu-mozilla-security/ppa

Then close the dialogue boxes and reload Synaptic. You will be able to upgrade FF to version 3.6.11 (this is the stable version)

If you are more adventurous you can use daily build repo by adding instead > ppa:ubuntu-mozilla-daily/ppa


You will be able to get FF3.6.12 (it turns blue and changes its name to namoroka)and FF4 beta if you add the daily build repo.

---

### Post by ratcheer on 2010-10-20
> **BobJam said:**
> Is that going to be in the Canonical repository, or are you talking about strictly a download from Mozilla instead?

In FF 3.6.10, I just went to Help >> Check for Updates. It found and installed the 3.6.11 quickly and easily/

Tim

---

