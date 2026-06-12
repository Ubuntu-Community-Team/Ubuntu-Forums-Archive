---
title: "run out of harddisk space for ubuntu partition"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by adisi on 2009-07-01
i have run out of space on my ubuntu partition. i have 10gb unalloated space which i recently formated to ext3(dev/sda 4)  thinkin it will automatically be added to the ubuntu partition. but it did not turn out so..how do i add this space to the ubuntu...i am runnin both vista and ubuntu 9.04..thanks in advance

---

### Post by carml on 2009-07-01
If you have got s LiveCd of Ubuntu or Gparted LIve,just boot with the cd into the drive,then delete the last partition you created and expand the partition of Ubuntu selecting the button move/delete.
If you need more explanations you have only to ask them. :)

---

### Post by adisi on 2009-07-01
thanks carml but i think iwill need further explanation on how to do those..i am kinda new you know

---

### Post by carml on 2009-07-01
Don't worry,if you have got a cd with desktop in the name of the .iso you used to install Ubuntu,just insert it into your DVD drive,restart the pc,then when it load Ubuntu from the cd,choose your language and wait until appears something like the screenshot attached.
Once  you see that go to System->Administration->Partition Editor and follow the instructions I gave you in my previous post.

---

### Post by Elfy on 2009-07-01
I'll just add that if you do that you will need to make sure of a couple of things

1 - make sure that swap is off - you can do so from the Partition Editor - right click the swap partition - the option is there

2 - in order to add unallocated space to the existing linux partition it has to be next to it - you might need to start moving things.

If you are unsure once you start the editor - do a screenshot and post it here

---

### Post by carml on 2009-07-01
> **forestpixie said:**
> I'll just add that if you do that you will need to make sure of a couple of things

1 - make sure that swap is off - you can do so from the Partition Editor - right click the swap partition - the option is there

2 - in order to add unallocated space to the existing linux partition it has to be next to it - you might need to start moving things.

If you are unsure once you start the editor - do a screenshot and post it here

Thanks, I'm used to GpartedLive,because I used an alternate cd to install.

---

### Post by Elfy on 2009-07-01
I don't use either - PartedMagic for me :)

---

### Post by theDaveTheRave on 2009-07-01
[QUOTE=adisi]i have run out of space on my ubuntu partition. i have 10gb unalloated space which i recently formated to ext3(dev/sda 4) thinkin it will automatically be added to the ubuntu partition. but it did not turn out so..how do i add this space to the ubuntu...i am runnin both vista and ubuntu 9.04..thanks in advance[/QUOTE]


you need to look into the mount command.

check out [this thread]("http://ubuntuforums.org/showthread.php?t=283131") by bhodi.zazen, he (and others onthe thread) helped me loads when I was setting up auto mount of various additional disks.

follow his instruction carefully, they should get things working. Look throught the other posts also, I know that I have a number of posts on this thread.

If you are in real striffe I recomend the the various IRC channels (this is the [list of IRC]("https://help.ubuntu.com/community/InternetRelayChat") chat channels, with instructions for how to connect.

You did the right thing with posting a new thread, and I think that the assistance by carml will get you sorted out, the thread by bodhi may scare you a little bit as it is a lot of command line stuff... but try to work through it, it is interesting to see how this works (as far as I am aware the procedure that you would take with the GParted would most likely end up giving a similar structure to the various config files - please someone correct me if I'm wrong ):P ).

I heartily recomend the IRC channel ubuntu-beginners ~ bodhi.zazen is an "ubuntu jedi" (or something or other) and if he isn't on the channel I'm sure someone else there will be able to help.

Unfortunately I'm not at my usual location (I'm just finishing a 2 week stint at my research institute), so I'm not going to be able to be as helpfull as usual.

carml and forestpixie....

I am wondering if there could be a suggestion in the idea pool for an automatic detection method for newly inserted HDDs and have a graphic open to configure their mount point, as I feel that this is probably a fairly common issue.

do you think that this is a common enought <issue> to require such an enhancement??

in fact I'm heading over there now to suggest.... the worst that can happen is that they say... no, not required  ;)

David

---

### Post by carml on 2009-07-01
I didn't install yet new hardware on my machine,so I don't know if there's some luck of easy-to-use feature.:?
When I can I post the GUI mode to get things work,so the newbies can feel better :).

---

### Post by theDaveTheRave on 2009-07-01
carml.

I understand the reasoning behind the GUI instructions.

As I say I was going to post in the ideas-pool thread... but can't seem to find it anymore??, or was it on launchpad?

So remember all you newbies, even a relatively experience user (take that comment with a heavy pinch of salt :lolflag: ) can forget where something lives!

David

_______edit________

so I found the idea pool... well sort of.

follow this [link ]("http://brainstorm.ubuntu.com/ideas_in_preparation/#") to the web page for new ideas to be added.

---

