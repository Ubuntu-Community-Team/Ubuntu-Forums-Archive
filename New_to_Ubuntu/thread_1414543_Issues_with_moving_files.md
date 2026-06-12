---
title: "Issues with moving files"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by joeshmoe5409 on 2010-02-23
I'm very new to Ubuntu.  I just installed karmatic on an old mac g4 tower that I had laying around that I want to start using as a general-use computer and to get a little more familiar with using terminal.

One of the first things I did is find the applications folder, look up how to bring up a root user window, and (because I have a bit of a thing for organization) start making folders within 'applications' such as 'games', 'openoffice', and 'preferences'.  I noticed as I started moving preferences applications into said folder, they started disappearing from the list of options in Control Center.

This doesn't surprise me in the least, because I'm changing their location and Control Center doesn't know where to look for them.  Is there a way to change the folder Control Center looks in for the various preferences applications? Or should I just abandon my attempts at cleanliness, suck it up, and just deal with long lists of applications?

---

### Post by ankspo71 on 2010-02-23
Hi,
Are you saying that you are wanting to reorganize system files such as the files in /usr/bin ? I have a feeling that would require alot of work. If you were able to reorganize this, every future program you install would ruin that new layout, and may not even work. 

When I open the "control center" in ubuntu 9.10, I see six categories. Are you wanting to create more or different categories? I'm sure it could be done, but I believe it would require editing *.desktop and *.directory files. I also think that this would be alot of work.

Or are you wanting to reorganize the start menu's list of applications? 
 This is easier using the start menu editor (alacarte). You can make as many directories and menu entries as you like.

Hope this helps.

---

### Post by mechro on 2010-02-23
In effect, what you're attempting there is equivalent to creating your own Linux distro and it wouldn't be Ubuntu anymore. There are certain Linux filesystem conventions as to where stuff goes which Ubuntu follows to a great extent.

The fact that you've had to log in as root/admin to perform these actions gives you the clue that these are system folders/files and it's advisable not to mess around with them until you've got more experience of the system.

You have more freedom in your Home folder to do as you please but even in there you couldn't put all your hidden configuration files in, for example, a Configuration folder without a lot of tweaking.

As ankspo71 has said, you could rearrange your Application/Places/System Menu to your liking.

---

