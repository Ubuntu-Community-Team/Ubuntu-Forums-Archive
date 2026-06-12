---
title: "Partition Chaotic"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by Arifcatalyst on 2011-05-21
Well!!! I was using Ubuntu Through Wubi installer..After Using a while I decided to install it on a separate partition.

SO....my question arises here-
1)I wanna install Ubuntu on my E partition so that all the data remains in it. It is formatted with Ntfs File format!!!
2)so what i gonna have to do To install Ubuntu On it except the choice of formatting whole partititon.(I know that :P)
3)Can't we just Extract free Space From that drive and format it through ext4 partition!! and just install Ubuntu.And then same for swap!!

Plzzz DonT Give links to Tutorial..i have alraedy Read It Thousand times!!!

Just gimme The Answers Of Theez Questions!!!
Thanxxx

---

### Post by xdragonforce on 2011-05-21
> **Arifcatalyst said:**
> Well!!! I was using Ubuntu Through Wubi installer..After Using a while I decided to install it on a separate partition.

SO....my question arises here-
1)I wanna install Ubuntu on my E partition so that all the data remains in it. It is formatted with Ntfs File format!!!
2)so what i gonna have to do To install Ubuntu On it except the choice of formatting whole partititon.(I know that :P)
3)Can't we just Extract free Space From that drive and format it through ext4 partition!! and just install Ubuntu.And then same for swap!!

Plzzz DonT Give links to Tutorial..i have alraedy Read It Thousand times!!!

Just gimme The Answers Of Theez Questions!!!
Thanxxx
1. Great. Do you already have windows installed In E:/? If not then choose that at the installer 
2. If you want to install Ubuntu it needs its own partition. If u want to create a smaller partition then boot into a LiveCD and use gparted to create a new partition.
3. No idea what you mean by 'extract free space'

---

### Post by Arifcatalyst on 2011-05-21
> **xdragonforce said:**
> 1. Great. Do you already have windows installed In E:/? If not then choose that at the installer 
2. If you want to install Ubuntu it needs its own partition. If u want to create a smaller partition then boot into a LiveCD and use gparted to create a new partition.
3. No idea what you mean by 'extract free space'

No!!! Windows isnt install on that partition.

BUt, We cant create more than four partition!!(correct me if I'm Wrong)

"Extract Free Space".. i meant that What Z shrinking And Expanding...is It smthing related with Creating NEw Partition!!

---

### Post by wep940 on 2011-05-21
Hey, first off, simmer down! It isn't that important that you need to be upset about it as you appear to be.
 
Take a look at what the disk manager does in the LiveCD installation process: you can shrink a partition and allocate that freed space to ubuntu. It sounds to me like that is what you are asking. By selecting the manual partitioning option, so you specify which drive you want to use. If you are going to use the equivalent of your Windows "E" drive, then you will also want to be sure you put the grub boot loader in the correct place, since "E" most probably is not the boot drive.  If this is just another partition but on a single disk with Windows, booting should be handled automatically by the installation procedure.
 
Example of the repartitioning from the LiveCD installation process:
 
Start with:
 
volume "x":
 
<------------------------------------------- NTFS ------------------------------------------->
 
Then with manual partitioning:
 
- shrink the NTFS partition:
 
<----------------------- NTFS ----------------------------------><---- free space -------->
 
- define a new partition as swap in the free space (see note about size below):
 
<----------------------- NTFS ----------------------------------><swap><--free---------->
 
- define a new partition as ext4 partition in the free space:
 
<----------------------- NTFS ----------------------------------><swap><---- ext4 ----->
 
 
Now for a couple of things you need to be aware of before doing any of this:
 
- run the Windows defrag utility on the drive you are going to use - 2 times is better, right before you start the repartitioning
 
- when you use the installer disk partitioner your NTFS data is preserved
 
- your swap file size is a variable thing - not a laptop? Don't plan on hibernation? Have a couple of gig of memory? Make swap small - say 512mb.

---

### Post by Arifcatalyst on 2011-05-21
But I M saying we cannot create MOre than four partition..
And what is intaller disk partition!

How??? :confused:

---

### Post by Lateralis on 2011-05-21
You cannot create more than 4 *primary *partitions, but you can create multiple *logical* partitions inside a primary *extended* partition.  

I know you said that you've already read the guides and so don't want any more posted links, but if you have read the [Ubuntu HowTo partitioning guide]("https://help.ubuntu.com/community/HowtoPartition") then you would know about extended and logical partitions, and wouldn't have these questions.  So I strongly recommend you follow the links on the page I've linked to in this post.  If you're still unsure what to do then feel free to ask specific questions.  

Also, to help with further answers, you might want to say which version of Windows you're using and how your drive is currently set up.  That means telling us how many partitions you have, how big they are and what function they perform, i.e. Windows system partition, Windows recovery partition, data storage etc...  That will enable us to tailor our answers to your specific set up.

---

### Post by prshah on 2011-05-21
> **Arifcatalyst said:**
> 
1)I wanna install Ubuntu on my E partition so that all the data remains in it. 

Plzzz DonT Give links to Tutorial..i have alraedy Read It Thousand times!!!


You can use LVPM to move your ubuntu install over to a dedicated partition; 
Take a look at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

I have to give you a link because there is much information that needs to be read before you can use this.

Hope this helps.

---

### Post by wep940 on 2011-05-21
> **Arifcatalyst said:**
> But I M saying we cannot create MOre than four partition..
And what is intaller disk partition!
 
How??? :confused:
 
Please, as much as you said you don't want any links you just want to know how to do this, you really do need to read up on partitions, primary, extended and logical. You also need to read up on the actual installation process using the LiveCD.
 
Basically, you need to educate yourself more. And PLEASE, no more exclamation points, capitalized print, etc. -> it gives the impression you are mad, and most of us interpret a mad person as not being as open as they need to be to suggestions from those trying to help them.
 
So, why don't you take a day or two to research partitioning and the actual Ubuntu installation process. There are sites on the net that actually show the process step by step with screen shots. There are even some videos on you-tube. But the thing is, you need to do that yourself - we can't do it for you.
 
After that research, you will be more educated on what needs to be done and what will happen, so you should feel much more comfortable with all of this, and with conversing with those of us trying to help you. Once you've done the homework, post back and people will be happy to help!
 
Best of luck! ;)

---

### Post by Arifcatalyst on 2011-05-21
> **wep940 said:**
> Please, as much as you said you don't want any links you just want to know how to do this, you really do need to read up on partitions, primary, extended and logical. You also need to read up on the actual installation process using the LiveCD.
 
Basically, you need to educate yourself more. And PLEASE, no more exclamation points, capitalized print, etc. -> it gives the impression you are mad, and most of us interpret a mad person as not being as open as they need to be to suggestions from those trying to help them.
 
So, why don't you take a day or two to research partitioning and the actual Ubuntu installation process. There are sites on the net that actually show the process step by step with screen shots. There are even some videos on you-tube. But the thing is, you need to do that yourself - we can't do it for you.
 
After that research, you will be more educated on what needs to be done and what will happen, so you should feel much more comfortable with all of this, and with conversing with those of us trying to help you. Once you've done the homework, post back and people will be happy to help!
 
Best of luck! ;)

DudE!!!Thanxxx For Teh Motivitation!!!)

THEre are some stuff that are needed to be learn by itself!!!

I wud give it as shot...btw... it z has became a nightmare for me now...Will kick this out soon

---

### Post by wep940 on 2011-05-21
It would seem that perhaps English isn't your primary language, so I admire you for even being able to converse with us - I have never been able to learn another language and I envy those who can and do.
 
I also hope you understood my last post wasn't meant to be demeaning or anything like that, but rather things I thought might help you so we can help you - nothing bad was intended!
 
Let us know when you are ready, and we'll be here!
 
Dave ;)

---

