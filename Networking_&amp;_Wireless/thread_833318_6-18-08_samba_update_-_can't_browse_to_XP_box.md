---
title: "6-18-08 samba update - can't browse to XP box"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by brutalandkind on 2008-06-18
I am using Ubuntu 8.04 and have a network of 3 machines total, 2 XP and this Ubuntu box. I ran the prompted update this morning and suddenly cannot browse one of my XP machines via Nautilus. The share name that used to appear doesn't appear at all, though the other XP machine shows up as it did before.

When I ran the aforementioned configuration update it prompted me at one point (I can't remember the precise text of the message) to choose between my existing samba conf and an "updated" one; I meant to choose the existing one but clicked on "Cancel." It prompted me again and then I chose to keep the existing one. Right after the routine finished updating my system, one of my XP machines was invisible to the network. 

I ran "pgrep -l mbd" and the result was this:

5185 nmbd
5187 smbd
5322 smbd

(I actually have no idea what that means, Jetsam suggested I include the output of the command in a new post, so here I am).

If there's any other info I can provide that might help, I'd be happy to do so. Thanks in advance.

---

### Post by jetsam on 2008-06-18
The pgrep command searches for running processes with "mbd" in their names.  It shows that smbd and nmbd, the two important  samba daemons, are both running like they should be.  

Today's Samba update was a security update.  It has to do with network browsing so it very well could be at fault.  

You should try a few things first:
--Reboot the Ubuntu computer, and then the xp computer.  When you updated Samba, it was necessary that Samba get restarted.  Sometimes this can cause browsing to get out of whack.  It's possible a few simple restarts and waiting for 15 minutes could clear this up.  Netbios browsing can be flaky that way.  

--Open Nautilus and and try typing:
```
smb://[COLOR="Blue"]servername[/COLOR]/
``` 
Into the location bar.  Replace [COLOR="Blue"]servername[/COLOR] in the above with the name of the windows computer you are trying to browse.  If you can't see a location bar, toggle it on by hitting the little pencil and paper icon underneath the back button.  
Can you browse the computer that way?  This isn't ideal, but it's better to have a work-around than not.  

--If that doesn't work, try the same thing with:
```
smb://[COLOR="Blue"]ip.ad.re.ss[/COLOR]/
```
...and replace [COLOR="Blue"]ip.ad.re.ss[/COLOR] with the ip address of the windows computer.  Does it work that way?

--type this:
```
smbtree
```
in a terminal, and hit enter when it asks for a password.  Does your XP computer and its shares show up in the output?  If there are any error messages in it, post the output here.  

Hope that helps...  If restarting doesn't fix browsing, there are some other more technical things to try.  These problems can be tricky, though...

---

### Post by brutalandkind on 2008-06-18
> **jetsam said:**
> The pgrep command searches for running processes with "mbd" in their names.  It shows that smbd and nmbd, the two important  samba daemons, are both running like they should be.  

Today's Samba update was a security update.  It has to do with network browsing so it very well could be at fault.  

You should try a few things first:
--Reboot the Ubuntu computer, and then the xp computer.  When you updated Samba, it was necessary that Samba get restarted.  Sometimes this can cause browsing to get out of whack.  It's possible a few simple restarts and waiting for 15 minutes could clear this up.  Netbios browsing can be flaky that way.  


Jetsam --

The double-secret-reboot seems to have done the trick! I had to reboot each machine twice (and waited half an hour the second time) but after that the second XP machine reappeared in the network list.

I hugely appreciate the info and the time you took to help. Almost wish I'd have needed to dig a little deeper to fix it (I know, careful what you wish for <g>).

P.S. I tried running smbtree and got a partial listing but also the following error: cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine NEW.  Error was NT_STATUS_ACCESS_DENIED

So apparently even though I can browse files now through Nautilus, there's still some stuff awry; I'll try your other suggestions and see what develops. Again, your help was *hugely* appreciated.

---

### Post by jetsam on 2008-06-18
Sure.  Glad you got it (mostly) working.  :)

I did a Google search on some key terms in that error message and got a bunch of hits, but none of them offered much clarity and light...

It seems possible that it could be caused if, on the machine NEW, you have the guest account disabled, you haven't enabled file and print sharing, or if some of the shares on the machine are not guest accessible because of Windows permissions settings.  

If Nautilus is working, though, and you have the functionality you want, you might be best off leaving well enough alone.  Sometimes it's best in this particular area not to push your luck.  :wink:

---

### Post by brutalandkind on 2008-06-19
> **jetsam said:**
> Sure.  Glad you got it (mostly) working.  :)

I did a Google search on some key terms in that error message and got a bunch of hits, but none of them offered much clarity and light...

It seems possible that it could be caused if, on the machine NEW, you have the guest account disabled, you haven't enabled file and print sharing, or if some of the shares on the machine are not guest accessible because of Windows permissions settings.  

If Nautilus is working, though, and you have the functionality you want, you might be best off leaving well enough alone.  Sometimes it's best in this particular area not to push your luck.  :wink:

Ha! Point well taken. I had much the same experience searching via Google, though my comprehension of even the basic samba settings could definitely use some improvement.

In any event, thanks again for your assistance and expertise. As noted, it's all extremely appreciated.

---

