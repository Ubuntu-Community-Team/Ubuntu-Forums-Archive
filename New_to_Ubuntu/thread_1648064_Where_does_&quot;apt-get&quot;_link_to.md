---
title: "Where does &quot;apt-get&quot; link to?"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by Miter_J on 2010-12-18
It is amazing that we can install a variety of softwares just by 
  <code>sudo apt-get install something</code>
  So I'm very confused about how the system know where to download the software we're asking for?
  Does it just search in apt-get.org?
  Btw, is apt-get.org an unofficial website? Why should we download most of our common softwares there?

---

### Post by Linux_junkie on 2010-12-18
It is an Ubuntu app (or maybe Debian) that links to their servers for downloading updates and new software that becomes available for Ubuntu.

---

### Post by hwychld on 2010-12-18
The link below should explain a bunch.  Basically Ubuntu keeps a list of servers to check for software.  This list is found in /etc/apt/sources.list.  You have the ability to add sources if you so chose (just make sure you trust them).

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by cgroza on 2010-12-18
Apt has a file called sources.list in wich servers and repositories are listed. Each time when you do sudo apt-get update apt gets a list of packages available in those repositories.
There is no magic, it has well defined places where to look and you can add repositories yourself to extend the available software.

---

### Post by oldos2er on 2010-12-18
> **cgroza said:**
> Apt has a file called sources.list in wich servers and repositories are listed.

And more lists may be kept in /etc/apt/sources.list.d/

---

### Post by Miter_J on 2010-12-18
> **cgroza said:**
> Each time when you do sudo apt-get update apt gets a list of packages available in those repositories.
There must be lots of packages which we do not use that exist in those repositories. So when we "update" them, what indeed were updated? Are those the packages that we already have and whose versions are older that are updated? If what I think is right, the updating process will ignore those packages which we didn't have at all, is it?

---

### Post by CharlesA on 2010-12-18
> **Miter_J said:**
> There must be lots of packages which we do not use that exist in those repositories. So when we "update" them, what indeed were updated? Are those the packages that we already have and whose versions are older that are updated? If what I think is right, the updating process will ignore those packages which we didn't have at all, is it?

Running:

```
sudo apt-get update
```

Updates the index of available packages.

```
sudo apt-get upgrade
```

Updates installed packages.

---

### Post by akand074 on 2010-12-18
> **Miter_J said:**
> There must be lots of packages which we do not use that exist in those repositories. So when we "update" them, what indeed were updated? Are those the packages that we already have and whose versions are older that are updated? If what I think is right, the updating process will ignore those packages which we didn't have at all, is it?

What CharlesA is saying simply is yes. Only packages you already have installed and has a newer version, gets updated.

---

### Post by Miter_J on 2010-12-18
> **CharlesA said:**
> Running:

```
sudo apt-get update
```

Updates the index of available packages.

```
sudo apt-get upgrade
```

Updates installed packages.

Sorry, but what does "index" mean? I'm really new here.:P

---

### Post by CharlesA on 2010-12-18
> **Miter_J said:**
> Sorry, but what does "index" mean? I'm really new here.:P

It's just the list of what packages are available in the repositories.

---

### Post by Paqman on 2010-12-18
The package manager maintains a list of what packages are available, and what version number they are. If the packages that you have installed are the latest versions it thinks are available, then it won't try to update anything. If you update your sources list (through sudo apt-get update or the update buttons on the graphical tools like Update Manager or Synaptic) and the system sees that there are now newer versions available, it will offer to upgrade them.

---

### Post by 73ckn797 on 2010-12-18
> **Miter_J said:**
> Sorry, but what does "index" mean? I'm really new here.:P
The index is just like a book. It lists what is available in the contents of the particular publication. If you have enabled repositories then the command [HTML]sudo apt-get update[/HTML] reads the currently available programs. See the attached images for the enabled repositories.  (mine may differ slightly) Go to System/Administration/Software Sources for the place to enable the sources.

---

### Post by Miter_J on 2010-12-18
> **CharlesA said:**
> It's just the list of what packages are available in the repositories.
Does Ubuntu save a list (that's the "index") in this computer?
If so, when checking for updates, does Ubuntu check it in the list that is stored locally or in the list on the online repositories?

---

### Post by 73ckn797 on 2010-12-18
> **Miter_J said:**
> Does Ubuntu save a list (that's the "index") in this computer?
If so, when checking for updates, does Ubuntu check it in the list that is stored locally or in the list on the online repositories?
It reads the online then updates the stored list.

---

### Post by Miter_J on 2010-12-18
> **73ckn797 said:**
> It reads the online then updates the stored list.
Then what's the use of the stored list?

---

### Post by CharlesA on 2010-12-18
> **Miter_J said:**
> Then what's the use of the stored list?

If there are no new updated packages, there is no reason to update the stored index.

---

### Post by 73ckn797 on 2010-12-18
> **Miter_J said:**
> Then what's the use of the stored list?
It is the last stored list of what programs or updates you currently have. Update will compare that to any changes online and recommend upgrading as necessary. Call it a dynamic indexing system.

---

### Post by Miter_J on 2010-12-18
> **CharlesA said:**
> If there are no new updated packages, there is no reason to update the stored index.
My question is, why should this local list exist?
When checking for new updates, what we search in is the online list and we do not refer to this list at all.

Btw, there must be a list which displays the current version of the packages installed here as well, right?

---

### Post by Miter_J on 2010-12-18
> **73ckn797 said:**
> It is the last stored list of what programs or updates you currently have. Update will compare that to any changes online and recommend upgrading as necessary. Call it a dynamic indexing system.
So I might have misunderstood.
The local index stores the current version of the installed packages instead of the latest version online. Is it?

---

### Post by CharlesA on 2010-12-18
> **Miter_J said:**
> My question is, why should this local list exist?
When checking for new updates, what we search in is the online list and we do not refer to this list at all.

Btw, there must be a list which displays the current version of the packages installed here as well, right?
Synaptic shows the version numbers.

---

### Post by Miter_J on 2010-12-18
> **CharlesA said:**
> Synaptic shows the version numbers.
Still confused.
What function does the stored list have?
I just think that it is not necessary for the localhost.

---

### Post by 73ckn797 on 2010-12-18
> **Miter_J said:**
> So I might have misunderstood.
The local index stores the current version of the installed packages instead of the latest version online. Is it?
Yes.

This how it is.

---

### Post by 73ckn797 on 2010-12-18
> **Miter_J said:**
> Still confused.
What function does the stored list have?
I just think that it is not necessary for the localhost.
I perceive that you are concerned about something that is not important. This is just how things are (As I stated in previous reply). Update only does just that. Upgrade applies the changes that apply to what you already have. Many updates are security issues. Some are recommended changes to additionally installed apps that are simply updates and not related to a security concern.

---

### Post by Miter_J on 2010-12-18
Thank you for your patience, 73ckn797.
Also, thanks to CharlesA and all the answerers above.
:D
Learned a lot from all you guys.

---

### Post by Miter_J on 2010-12-18
73ckn797, I've got two more unsolved problems and I wonder whether you'd like to help me out?
1.How to play fullscreen videos in console?  I have tried "mplayer -vo fbdev -fs test.avi" as well as "mplayer -vo fbdev -screenw 800 -screenh 600 -fs -zoom test.avi" but neither of them changed the size of the display screen. The display range is still very small.
2.Could Chinese characters shown in the console? All I get in the console is a block instead of the Chinese character

---

### Post by 73ckn797 on 2010-12-19
> **Miter_J said:**
> 73ckn797, I've got two more unsolved problems and I wonder whether you'd like to help me out?
1.How to play fullscreen videos in console?  I have tried "mplayer -vo fbdev -fs test.avi" as well as "mplayer -vo fbdev -screenw 800 -screenh 600 -fs -zoom test.avi" but neither of them changed the size of the display screen. The display range is still very small.
2.Could Chinese characters shown in the console? All I get in the console is a block instead of the Chinese character
These are questions that I cannot answer. I never have dealt with them. I recommend starting a new thread to address these items. Post it in the Multimedia section.

---

### Post by Miter_J on 2010-12-19
Thanks.  I've got one of them answered.

---

### Post by 73ckn797 on 2010-12-20
If this thread is considered solved you can mark it so from Thread Tools, above your first post. That flags it and will help someone else with similar questions.

---

### Post by Miter_J on 2010-12-21
OK.
Thank you.
I didn't know that.
I'll do it immediately.

---

