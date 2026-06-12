---
title: "Restore installed applications from a previous root.disk?"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by FlameReaper on 2010-08-27
Hello, I'm just curious about something that has been bothering me a while...

A noob question/problem: I wonder if it is actually possible for me to restore applications and settings I had in a previous Ubuntu installation to a new one? This question also applies for Wubi-based installations which is the main method I'm using to have Ubuntu in my laptop. Here are some conditions I need to consider in order to get things working again, and to be frank with these in mind I'm kinda in a deadlock about it:

1. I don't have any cached packages, as my habit everytime I install a software is to run sudo apt-get clean, which clears the /var/apt/archives cache from the computer. Pretty much leaving me with none.

2. I am under the severe inability to get connected to the Internet, due to my line being an extremely slow residential college line which only barely lets me do some basic surfing.

3. With point no. 2 it is likely that if I need any additional software/utility to work on it I'll be unable to get them and I don't have the luxury of time for that...

4. I already uninstalled my previous Ubuntu installation leaving only the root.disk and swap.disk, and no I can't just make them replace the new installation as for some reason there's something wrong in it that causes my installation to drop to BusyBox everytime I try to boot from it. All I need are my applications and settings, bear that in mind.

5. And now for the actual silly point I'm thinking of wanting to do: Can't I just copy paste the specific folders which contains all my installed applications and their settings to my new installation? Somehow I tried it and it worked before; although I can't be too sure about that since I only tested it on just *one* software (which is Kate).

Basically what I'll be having in order to attempt this restoration of installed apps and settings will only consist of:

1. The old root.disk and swap.disk
2. A new Ubuntu installation (in my case, from Wubi, though any applicable solution is accepted)
3. NO INTERNET CONNECTION! Must be able to be done offline :(
4. <further stuff in the list to be updated when situation calls for it> 

Oh, just as a reminder: Assume that I already have my /home/ directory backed up. Even if I didn't, I'll do it first before all the other stuff ;) Also I know how to mount the root.disk image to be read from another Ubuntu installation/the live disk, so please skip on telling me how to do it :)

---

### Post by FlameReaper on 2010-08-27
Bump...

---

