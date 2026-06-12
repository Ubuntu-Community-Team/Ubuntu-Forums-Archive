---
title: "New to Ubuntu (my very first post here!)"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by LaughingOne on 2009-02-10
Hello world!

Sorry about that, couldn't resist.

I just installed Ubuntu 8.10 64bit Desktop on my main rig last night. I am a avid web surfer, video watcher, skype user, folder, and game player which was why I was running Vista 64bit for quite some time. Last night on a whim, I installed Ubuntu. I gotta say this is a whole different animal and using the terminal on a constant basis (or at least for now) seems to be the norm.

I think I got lucky though because I did quite a bit of googling while running the Live CD before doing the actual install. I found generic answers to installing onto a Fakeraid and on how to get the newest Nvidia graphics drivers installed. I successfuly did both within a few hours. i even got my multi-monitor setup working as well! :)

So I'll probably be asking some questiions shortly on how to do a few specific things relating to my normal computer habits. But anyhow, I'm glad to be joining the Ubuntu community. If I can stick with this for a few months, I'm sure I'll be a user for life!!!

---

### Post by kellemes on 2009-02-10
It's a different animal indeed..
Glad to hear you like it and are able to get things done this quick.
Pretty impressive, it took me about 400 years to get things done ;-)
Good luck and ask questions when needed.

---

### Post by donkyhotay on 2009-02-10
If you've been using windows for a long time linux is *very* different and many things you take for granted are completely different. Once you get the hang of it though you see that it's actually quite logical and efficient way of doing things. Although I'm still proficient in windows I find it a little bit strange to work with because it's not as intuitive. For example a lot of people compain about having to edit text files however I would much rather now edit text files then windows registry keys.

---

### Post by jimv on 2009-02-10
I noticed that you said you used Skype.

Here's how to get Skype in Ubuntu:

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

Also, to get all your videos, music, and Flash stuff working correctly, you'll need to install a package called 'ubuntu-restricted-extras'

The easiest way (in my opinion) to install things is through the terminal.  Open a terminal window (Applications > Accessories > Terminal) and type this:

sudo apt-get install ubuntu-restricted-extras

---

### Post by LaughingOne on 2009-02-10
Ah thanks for that info jimv. I installed Skype last night and got it working, but I think I installed the 32bit version. I had to install some other 32bit modules or lib files (can't remember what it was called) to get Skype to work in the 64bit environment.

When I get home from work, I'll uninstall my Skype and try out the steps outlined in the link you posted. Thanks!

---

### Post by sandyd on 2009-02-10
video watcher... hmm...might want to do this

```

sudo apt-get install ubuntu-restructed-extras

```
pulls in all codecs :)
or rather most of them.....

---

### Post by LaughingOne on 2009-02-11
Ah bummer. I can't figure out how to remove Skype. It's not listed in the Add/Remove Apps nor is it listed in the the Synaptic Package Manager thing. However, I got a one-fix-fixes-all solution for that. I'll be re-installing Ubuntu in a few days here because I should be getting my Adaptec 5805 card in the mail. After I get that puppy in there, then I'll just start from scratch again.

On a side note, I followed the instructions on getting video/multimedia playing from the Multimedia & Video room. I checked out all my anime collection and they load up fine but there is a slight audio sync issue going on. I'll visit that later.

I also got SMP and GPU2 folding clients running successfully. The SMP client folds nice and fast (even though it isn't maxing out my cores, weird) but the GPU2 folding client runs horribly slow compared to when it was running in Vista64.

For the next day or two I'll be reading up the how/what/why of recompiling apps and kernels until I get my new raid card to do my rebuild. Hopefully that can help iron out the little glitches I'm experiencing .

---

