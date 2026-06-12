---
title: "Windows installer"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by bobbydemos on 2011-08-13
Hi guys,

I went Ubuntu a while ago but reverted back to windows. I now have Ubuntu installed on my laptop and windows on my desktop, but I've still got windows on the laptop as well. I went to use the windows install again to install kubuntu and it will only let me install one instance. Is there anyway of getting round this? 

Thanks,

Bobby

---

### Post by snip3r8 on 2011-08-13
Are you attempting to install Kubuntu on your desktop or laptop?

---

### Post by kroq-gar78 on 2011-08-13
> **snip3r8 said:**
> Are you attempting to install Kubuntu on your desktop or laptop?
It shouldn't matter which computer he's using b/c he said he's on windoz.

Also, before I start, when you say "I went to use the windows install again to install kubuntu", do you mean WUBI? or do you mean the disk installer?

I've seen a thread about this somewhere on the forums a while ago (1-2 years). My guess is that you would rename the ubuntu.disk file in C:\ubuntu\disks\ to something else, and then make a copy of ubuntu.disk in the same directory, do some stuff with the windoz bootloader to make it show multiple entries (or something like that...)

I might be able to find the post somewhere on the Ubuntu Forums, but it may take a while.

Hope it helps...

---

### Post by snip3r8 on 2011-08-14
> **kroq-gar78 said:**
> It shouldn't matter which computer he's using b/c he said he's on windoz.

Also, before I start, when you say "I went to use the windows install again to install kubuntu", do you mean WUBI? or do you mean the disk installer?

I've seen a thread about this somewhere on the forums a while ago (1-2 years). My guess is that you would rename the ubuntu.disk file in C:\ubuntu\disks\ to something else, and then make a copy of ubuntu.disk in the same directory, do some stuff with the windoz bootloader to make it show multiple entries (or something like that...)

I might be able to find the post somewhere on the Ubuntu Forums, but it may take a while.

Hope it helps...

I asked which he was installing on because it seems to me that he is already dual booting off the laptop so I thought he might be installing on the pc ,but then why mention the laptop?

---

### Post by Elfy on 2011-08-14
From what I can see you can have only one wubi instance. 

You could install the kubuntu desktop inside the existing ubuntu one - assuming you have room. 

As wubi is not supposed to be a permanent thing, could be time to look to installing it properly.

---

