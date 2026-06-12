---
title: "Beginner-like questions of a long-time user"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by okok on 2010-10-15
I am a long-time user of Ubuntu, but not a knowledgeable one. The fact that in spite of this I have encountered no serious problems shows how generally well-made Ubuntu is. However, there are several questions for which I don't know the answers and would thank anyone who can enlighten me one them:

1. I am currently running Ubuntu 9.10 on a netbook. I upgraded to this verion from an older installation of eeebuntu. The upgrade was completed successfully, but during boot and shutdown, I still see the old eeebuntu logo. Why is this happening? What element of the operating system is this and why wasn't it changed? If I upgrade to 10.4.1 LTS, will this still remain the same?

2. I have been using Ubuntu 9.10 with GNOME for a long time. Recently I added XFCE, and I think it works slighly more smoothly on my netbook. At some point, the desktop I began to see while using XFCE was the same as I have in GNOME: same color, same icons in the same locations, which are different from those I set in XFCE. Why is this happening?

3. While using GNOME I used the metacity configuration utility to set up a keyboard shortcut that runs a certain script. I know how to create a taksbar launcher in XFCE to run that script, but how can I set a keyboard shortcut for it?

Thanks in advance

---

### Post by SpockVulcan on 2010-10-15
I can answer question number 1:
In terminal type the following:

sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by okok on 2010-10-15
> **SpockVulcan said:**
> I can answer question number 1:
In terminal type the following:

sudo apt-get update && sudo apt-get dist-upgrade

Thank you, but my questions there were not how do perform an upgrade. I know how to do that. The only part of the question that had anything to do with upgrading was whether the part of the OS that is still a relic from eeebuntu - what I see when the system starts or shuts down - will change after an upgrade, as this was not changed in the previous upgrade I performed (from eeebuntu to 9.10).

All of my questions here are mostly not 'how to' questions, but attempts to understand how things work.

---

### Post by coffeecat on 2010-10-15
> **okok said:**
> I still see the old eeebuntu logo. Why is this happening? What element of the operating system is this and why wasn't it changed?

That's the usplash and it was last used in 9.10 to be replaced by Plymouth in 10.04.

Here's a useful link:

[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash)

You'll have to do a search in Synaptic to find the exact artwork package you need, but I think this was called ubuntu-artwork-usplash. It might already be installed if you did an upgrade to Ubuntu, but was simply not activated with a new initrd.img the way described in the link.

I'm sorry I can't help you with the Xfce questions.

---

