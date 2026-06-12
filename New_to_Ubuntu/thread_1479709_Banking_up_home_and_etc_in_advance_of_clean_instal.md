---
title: "Banking up /home and /etc in advance of clean install of lucid x64"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by Roger Allott on 2010-05-10
I've been using the 32-bit version of Ubuntu since 8.10 because the Windows version pre-installed on my machine was 32-bit so I just assumed that was what it could take. It was only when in a discussion on a thread here that I found out that my PC is 64-bit, so I decided to do a clean install of lucid x64 when it became available, as it now has of course.

I need to do some preparation in advance of the migration.

What I want to achieve is all of my current settings and preferences that I've grown to like in karmic x86 on my new lucid x64. If I understand the linux architecture correctly, most of these are in my home directory, but a few others are in my /etc folder.

Are there any other folders likely to have important settings and preferences information?

Backing up my home directory is pretty simple, but backing up the /etc folder causes me a few more headaches, as I need to preserve permissions I think, and whatever mechanism I use to restore /etc needs to respect those permissions.

Can anyone here help me with what I should do to achieve what I want?

Further, what order should I do things?

My current plan is:
[LIST=1][*]Clean install of lucid x64
[*]Apply any hardware drivers recommended
[*]Run Update Manager
[*]Set new Software Sources, to include Medibuntu and various other ones
[*]Install packages from a list of those that I have on karmic
[*]Restore home directory
[*]Restore /etc folder[/LIST]

How do I get a list of packages from karmic? I've tried:
```
dpkg -l
```
but that list is so long that I can only copy the ones from p-z. I've tried Save Markings As in Synaptic, but that just yields an empty text file of 0 bytes.

---

### Post by Temposs on 2010-05-10
Personally, I never backup my /etc folder. It's fine, and I like reset my system configurations in /etc since the new versions of the things you're configuring change significantly between versions.

For the list, try:

```
dpkg -l > package-list.txt
```

So, that will put the whole list in a file, and then you can scroll through the entire list. I also like forgetting what I had installed when I upgrade, personally, as it feels cleaner and I just install things as I need them.

---

### Post by Ozymandias_117 on 2010-05-11
I agree with Temposs, almost all of your configuration files are in /home. If you back up /etc too, you could end up causing problems depending on what packages are updated etc. So, while you may lose a few settings, you would have fewer headaches just skipping /etc.

---

### Post by Roger Allott on 2010-05-11
> **Temposs said:**
> Personally, I never backup my /etc folder. It's fine, and I like reset my system configurations in /etc since the new versions of the things you're configuring change significantly between versions.
There are two reasons who not porting my /etc would cause me problems. First is my need for the /etc/www folder that holds my local php web apps, and second is that the grub config settings stuff is in there somewhere.

I've set up Ubuntu to boot from an external HDD as Vista boots automatically when my external HDD isn't connected. It's very important that grub never tries to install an update or upgrade to my internal HDD.


> **Temposs said:**
> For the list, try:

```
dpkg -l > package-list.txt
```

So, that will put the whole list in a file, and then you can scroll through the entire list.
Thanks.

Is there any way of getting the list of just those packages that are 'top level' - ones that are not dependencies of any other package?

---

