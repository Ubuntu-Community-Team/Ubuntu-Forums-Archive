---
title: "partition issue for a noob"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by crowdedelevator on 2009-11-05
im a noob to linux ubuntu, so bear  with me, as im not the sharpest tool in the shed.
 
okay so i wanted to learn about ubuntu so i had a family member show me where to go to get it. 
 so i made a live cd of 9.04, and i popped it in, and made a small partition. a few weeks down the road and i figure i like it better.
 well, im new to partitioning as well, and i figured id get most of my harddrive and make it linux. well, i add all my music and video to linux, and use the boot cd to add space to linux.
it just  made another linux partition within the extension.

im not so smart. so i dont know how to get rid of it and make the space just the one linux. 
i can use gparted and erase the partition, but that leaves me with unallocated space within the extension. and im totally lost.
 email  me  at [EMAIL="stewart.scottlee@yahoo.com"]stewart.scottlee@yahoo.com[/EMAIL] 

thanks for helping me with this headache
[http://i858.photobucket.com/albums/ab143/thecrowdedelevator/Screenshot.png](http://i858.photobucket.com/albums/ab143/thecrowdedelevator/Screenshot.png)
its sda7
its within the ext, so when i delete it, it ext is stille there. i want to add the space to sda 5

---

### Post by ST3ALTHPSYCH0 on 2009-11-05
Back in a minute, need to get Gparted (you can put it into your install through synaptic) and refresh my memory.

---

### Post by ST3ALTHPSYCH0 on 2009-11-05
Alright, you will need to do this through the live CD so that you can keep your drive unmounted.
Open Gparted. Click on the partition you want to resize.
Make sure it's unmounted( right click and select unmount if it's mounted).
Click resize/move.
Click and drag the border.
Hopefully the free space is to the left of the partition, b/c I believe that there's problems expanding to the right. You might want to move the partition to the left if that's where the free space is and then resize.
_**As always, back up critical data before playing with partitions!!**_

---

### Post by crowdedelevator on 2009-11-05
so i just boot up on the live cd and go to the try ubuntu from disk and do it there, or what?
like i said, im not tech savvy.
and how do i back up these files?

---

### Post by YosefKaro on 2009-11-05
Yes, just boot into the live cd...it has gparted already on it.  As far as backup goes, if you have any critical data that you would hate to loose, you should always have that saved on a separate storage device eg external hard drive, DVD's or even mass storage USB sticks.

-Yos

---

### Post by ST3ALTHPSYCH0 on 2009-11-05
Yes to your first question.
I have to ask some questions to answer your second.
do you still have another partition or another hard drive besides the one Ubuntu is on?

---

### Post by crowdedelevator on 2009-11-05
thank you both, ill try it and get back. but no, i have my music on cd, but all i have is a few seasons  of spaced and a few emulators i really want to keep, but no worries on that

---

### Post by ST3ALTHPSYCH0 on 2009-11-05
You can always burn your stuff to CD or DVD. Odds are you won't have anything to worry about, but like I said, there's always a little risk when playing with partitions.

---

### Post by crowdedelevator on 2009-11-05
it wont let me do anything on the live cd .
its doing the same thing here. all i can do is delete the sda7 partition and it wont give any option to my ext or anything about mount/unmount.

---

### Post by crowdedelevator on 2009-11-05
oh you are all life savers. it was because of the location being the right as you mentioned. i thank you sooooo very much. you are awesome.

---

### Post by ST3ALTHPSYCH0 on 2009-11-05
I don't know what to tell you, I just fired up a jaunty live CD and Gparted would let me resize the primary partition to my little heart's desire. 
the sda7 number seems high, but let's wait til someone with more experience than myself chimes in.

---

### Post by crowdedelevator on 2009-11-06
i got it to work after i posted i couldn't( thus the thank you you are awesome post)
but it just gave me problems because for some reason it was really slow and didn't respond well. but i got it.

---

### Post by ST3ALTHPSYCH0 on 2009-11-07
No thanks necessary. I'm just glad it worked for ya.... hence the siggy :D

---

