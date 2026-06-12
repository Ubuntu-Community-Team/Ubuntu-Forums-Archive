---
title: "Should I be updating without testing?"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by RedOctober on 2010-03-01
I have about 10 Unbuntu 9.10 computers, which display the Update Manager almost every two days or so.  I have been proceeding with the updates without hesitation as I figure they are necessary and are already well tested by the Canonical and other Ubuntu people in the community.

Q1:  Should I be blindly trusting that the Ubuntu community has well tested these updates?

Q2:  Has anyone had or heard of a "bad update" where their computer crashed after updating?

Q3:  How are the updates screened and where do they come from?  Is it possible for a terrorist to purposely make a "bad update" that would pass Canonical and Ubuntu community testing, yet, on a certain date in the future, just destroy the OS and bring Ubuntu to it's knees, just to make headlines on CNN like "Ubuntu fails world wide" ???

---

### Post by medicalystoned on 2010-03-01
I have Kubunu 9.04, I update any time the computer tells me to and have never had a single bad thing happen because of it.  Hope that rings true for everyone else........ we have been with Ubuntu and other Linux distros for over three years now.......Peace

---

### Post by koba101 on 2010-03-01
I'm not sure if "terrorists" main priority is to release bad updates, but yes, testing is always useful...it' not just about the updates being "bad", it's more related to what works on your system or not.  

For example, I once had an update for brasero, and it turned out bad for my system because it was not compatible with another software (don't remember the exact details)....so i had to revert back to the old version, and ignore the update for the new one....such problems might happen, and in companies, or on production environments no sane system or security administrator would install updates without rigorous testing

what i do is have a version on virtualbox for testing, that should be useful for detecting any incompatibilities resulting from updates, especially kernel ones

it also depends on what type of update you have setup, only security , or a wider range

---

### Post by sandyd on 2010-03-01
> **RedOctober said:**
> I have about 10 Unbuntu 9.10 computers, which display the Update Manager almost every two days or so.  I have been proceeding with the updates without hesitation as I figure they are necessary and are already well tested by the Canonical and other Ubuntu people in the community.

Q1:  Should I be blindly trusting that the Ubuntu community has well tested these updates?

Q2:  Has anyone had or heard of a "bad update" where their computer crashed after updating?

Q3:  How are the updates screened and where do they come from?  Is it possible for a terrorist to purposely make a "bad update" that would pass Canonical and Ubuntu community testing, yet, on a certain date in the future, just destroy the OS and bring Ubuntu to it's knees, just to make headlines on CNN like "Ubuntu fails world wide" ???

1. Disable ubuntu backports and ubuntu proposed, and youll have well tested updates.

2. Only when messing with lucid.

3. Updates have a GPG key and a md5sum attached to each of them. If the file is modified, even one byte, the md5sum will be modified, and the update manager will not install it update.

---

### Post by 3rdalbum on 2010-03-01
Security updates are virtually 100% safe. "Recommended" updates are pretty safe. Before a "recommended" update appears in your update manager, it is tested by the Ubuntu developers, then pushed to users of the "Proposed" repository for testing, and then finally pushed to the rest of the community.

It's possible to have a bad one, but not likely. I've never had it happen to me.

The updates system is secure. Only Ubuntu developers have the ability to send updates to the main repositories. The Update Manager checks the authenticity of the repositories and the authenticity of each package as well, to prevent man-in-the-middle attacks.

Someone with malicious intent could start their own repository, encourage people to add it, and then send out an update to a core package, but the update would appear under the 3rd party repository's name, so you could smell a rat. This has happened before and Ubuntu's name hasn't suffered from it, because it's got nothing to do with Ubuntu.

---

