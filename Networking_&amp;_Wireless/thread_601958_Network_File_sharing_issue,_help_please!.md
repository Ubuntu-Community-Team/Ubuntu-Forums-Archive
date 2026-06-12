---
title: "Network File sharing issue, help please!"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by Eliphelet on 2007-11-03
Hi,

I have what I feel is quite a complex problem that I hope someone can help with.  

I have just installed Ubuntu on my pc which was amazingly simple and not at all like the horror stories ive heard.  I now have 2 physical HDD's in my desktop pc, one which hereon will be referred to as the Windows HD and the other the Ubuntu HD.  My windows HD has a number of partitions one of which holds a vast quantity of music, about 200gb of it.  

I have a standard home network with a combination of ethernet and wirelessly linked pcs round the house.  My brother who also listens to me does not have a great pc and could not hope to fit this music on the pc.  Before I started using Ubuntu the solution was simple, share the music partition on my windows xp HD over the network.  Doing this they could be effectively streamed round the house.

These files are stremed directly through windows media player and catalogued in the library there.  

When running windows on my pc this still works fine.  However when booting up Ubuntu I have no success whatsoever.  I have tried to find a guide that will help me sort this and have come up empty handed.  I'm hoping someone can tell me what i need to do this.  I have wondered whether the problem is that the music is on a completely different HD to the currently running OS but figure that regardless it must be possible to share the content of this drive over the network.

I also dont want my brother to have to type a password every time he tries to play a song.

I'd appreciate a set of instructions to do this or for someone to point the way to a guide that will help me.

Many thanks,

Eliphelet

---

### Post by jimrz on 2007-11-03
> **Eliphelet said:**
> Hi,

I have what I feel is quite a complex problem that I hope someone can help with.  

I have just installed Ubuntu on my pc which was amazingly simple and not at all like the horror stories ive heard.  I now have 2 physical HDD's in my desktop pc, one which hereon will be referred to as the Windows HD and the other the Ubuntu HD.  My windows HD has a number of partitions one of which holds a vast quantity of music, about 200gb of it.  

I have a standard home network with a combination of ethernet and wirelessly linked pcs round the house.  My brother who also listens to me does not have a great pc and could not hope to fit this music on the pc.  Before I started using Ubuntu the solution was simple, share the music partition on my windows xp HD over the network.  Doing this they could be effectively streamed round the house.

These files are stremed directly through windows media player and catalogued in the library there.  

When running windows on my pc this still works fine.  However when booting up Ubuntu I have no success whatsoever.  I have tried to find a guide that will help me sort this and have come up empty handed.  I'm hoping someone can tell me what i need to do this.  I have wondered whether the problem is that the music is on a completely different HD to the currently running OS but figure that regardless it must be possible to share the content of this drive over the network.

I also dont want my brother to have to type a password every time he tries to play a song.

I'd appreciate a set of instructions to do this or for someone to point the way to a guide that will help me.

Many thanks,

Eliphelet

Do you already have samba set up correctly and are able to share data files across your network? If not, see [[COLOR="Sienna"]**_this_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba") guide. Then follow [[COLOR="Sienna"]**_this_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=280473&highlight=smbmount") guide which will show how to mount your win share and, if desired, how to setup for it to mount automatically each time the machine is booted. This will allow for playing video over the network and greatly improve audio play back, as well.

---

