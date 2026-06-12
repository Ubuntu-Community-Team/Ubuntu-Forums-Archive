---
title: "Windows 7 ISO"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by frillybob on 2010-05-05
Is there a tool to copy my ISO of windows 7 just in case? I want to install Ubuntu and have but failed several times! Lucklily my recovery options were still there but I want to be sure.


P.S. free only who pays for something they use 1nce

---

### Post by madjr on 2010-05-05
Where did you fail to install ubuntu

it's straight forward process and wont harm your windows install, in fact is the best recovery tool in case something happens to it (like some virus, malware or registry error, etc.)

is as easy as this vid
[http://youtube.com/watch?v=Z0tNpt5RZYI](http://youtube.com/watch?v=Z0tNpt5RZYI)

or this guide
[http://dedoimedo.com/computers/ubuntu-install.html](http://dedoimedo.com/computers/ubuntu-install.html)

---

### Post by frillybob on 2010-05-05
long story any1 else

---

### Post by mechro on 2010-05-05
[http://store.microsoft.com/Help/ISO-Tool](http://store.microsoft.com/Help/ISO-Tool)

---

### Post by Jose Catre-Vandis on 2010-05-05
Do you mean you want to copy out your recovery partition? If so, you can do this using linux boot cds such as Clonezilla, Gparted or Parted Magic, all of which use the tool partimage in one way or another.

I have found you can easily copy a whole partition using gparted on the ubuntu live cd, you will need enough unallocated space on a HDD, preferably external.

That said, Ubunt is highly unlikely to destroy your recovery partition, as it is probably "hidden". If not you can hide it again using gparted on the live CD.

If you mean you want to copy an ISO file to disk, then use Brasero, or if you are in windows I would recommend the freeware program ImgBurn

---

### Post by frillybob on 2010-05-05
[http://store.microsoft.com/Help/ISO-Tool](http://store.microsoft.com/Help/ISO-Tool) thx but I didn't buy it from there!

---

### Post by shae on 2010-05-05
If you mean burn an ISO to disk, you can do that natively with Windows 7.

If you mean backup your installed version of Windows 7 to an installable ISO, I am not sure you can do that.  You can create an image of the disk that you could put back on there in case of a major problem.

---

### Post by frillybob on 2010-05-05
Do you mean you  want to copy out your recovery partition? If so, you can do this using  linux boot cds such as Clonezilla, Gparted or Parted Magic, all of which  use the tool partimage in one way or another.

I have found you can easily copy a whole partition using gparted on the  ubuntu live cd, you will need enough unallocated space on a HDD,  preferably external.

That said, Ubunt is highly unlikely to destroy your recovery partition,  as it is probably "hidden". If not you can hide it again using gparted  on the live CD.

If you mean you want to copy an ISO file to disk, then use Brasero, or  if you are in windows I would recommend the freeware program ImgBurn
 		                   		  		  		 		 			 				__________________


Thx!!!! I wanted to copy the iso of windows 7 and make it bootable like on a dvd or ... is that possible and if so which program. Sorry I know you probably already said it but I only know how 1 operating system runs and that's the PSP! I know little about the mechanics of a pc!

---

### Post by mechro on 2010-05-05
> **frillybob said:**
> [http://store.microsoft.com/Help/ISO-Tool](http://store.microsoft.com/Help/ISO-Tool) thx but I didn't buy it from there!

Yes, but doesn't the link explain how to make the ISO copy?

---

### Post by ubunterooster on 2010-05-05
[http://www.clonezilla.org/](http://www.clonezilla.org/)

I have a copy of vista on a spare drive using this. Not like I'll ever use Vista, but... just in case.

---

### Post by frillybob on 2010-05-05
[[IMG]http://ubuntuforums.org/customavatars/avatar922703_2.gif[/IMG]]("http://ubuntuforums.org/member.php?u=922703") 				 			  			 				 
				Join Date: Oct 2009
 				Location: UK
 				 	  					Beans: 907 				
 			       Ubuntu 9.04 Jaunty Jackalope  				 				 				 				 				    
 			
  	 	 	 	 		 		 			 			 				 				**Re: Windows 7 ISO** 			
 			 			 		   		 		 		 	Quote:
 	 	 		 			 				 					Originally Posted by **frillybob** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9244896#post9244896") 				
 				*[http://store.microsoft.com/Help/ISO-Tool](http://store.microsoft.com/Help/ISO-Tool)  thx but I didn't buy it from there!*
 			 		 	 	 
Yes, but doesn't the link explain how to make the ISO copy?




Where does it say that

---

### Post by mechro on 2010-05-05
> **frillybob said:**
> [[IMG]http://ubuntuforums.org/customavatars/avatar922703_2.gif[/IMG]]("http://ubuntuforums.org/member.php?u=922703") 				 			  			 				 
				Join Date: Oct 2009
 				Location: UK
 				 	  					Beans: 907 				
 			       Ubuntu 9.04 Jaunty Jackalope  				 				 				 				 				    
 			
  	 	 	 	 		 		 			 			 				 				**Re: Windows 7 ISO** 			
 			 			 		   		 		 		 	Quote:
 	 	 		 			 				 					Originally Posted by **frillybob** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9244896#post9244896") 				
 				*[http://store.microsoft.com/Help/ISO-Tool](http://store.microsoft.com/Help/ISO-Tool)  thx but I didn't buy it from there!*
 			 		 	 	 
Yes, but doesn't the link explain how to make the ISO copy?




Where does it say that

Well I'm not sure if I can fathom Microsoft's licensing conditions but I think you have to install Windows 7 by the process mentioned in the link and then you can make a copy of the ISO. Does that make sense??

---

### Post by frillybob on 2010-05-07
Any1???

---

### Post by ubunterooster on 2010-05-07
[http://www.clonezilla.org/](http://www.clonezilla.org/)
?

I mentioned it before but am not sure if you over looked it. Clonezilla copies a bit-by -bit clone of any partition or drive, in this case you will copy the windows partition.

---

### Post by QIII on 2010-05-07
Perhaps I missed your point after a couple of times reading through this  but:

1.  Do you want to copy a full install disk you have?

2.  Do you want to copy a recovery disk you got with the machine when  you bought it?

3.  Do you want to draw from your recovery partition on the drive as it  exists right now and somehow create an .iso from that?

4.  Do you want to make a full image of your drive as it is right now?

---

### Post by shindou01 on 2010-05-07
> **QIII said:**
> Perhaps I missed your point after a couple of times reading through this  but:

1.  Do you want to copy a full install disk you have?

2.  Do you want to copy a recovery disk you got with the machine when  you bought it?

3.  Do you want to draw from your recovery partition on the drive as it  exists right now and somehow create an .iso from that?

4.  Do you want to make a full image of your drive as it is right now?

I think he wants to do option number 3......If that is the case then why not try clonezilla?

or does anyone else have any other suggestions?

---

### Post by QIII on 2010-05-07
There is an option to create recovery disks through Windows itself.

---

### Post by djchandler on 2010-05-07
Decent OEMs provide tools to make a set of recovery DVDs. Sometimes there's actually worthwhile software installed by computer manufacturers.

Contact customer service for your computer manufacturer if you don't know where to find it or how to use it.

---

### Post by ubunterooster on 2010-05-07
> **djchandler said:**
> Decent OEMs provide tools to make a set of recovery DVDs. Sometimes there's actually worthwhile software installed by computer manufacturers.

Contact customer service for your computer manufacturer if you don't know where to find it or how to use it.

What about user data and user-installed data? And....all those bloated [size=7]"[COLOR="Red"]F[/COLOR][COLOR="DeepSkyBlue"]R[/COLOR][COLOR="Orange"]E[/COLOR][COLOR="Sienna"]E[/COLOR] Trial"[/size] programs that take precious time to remove if you reinstall via the OEM recovery discs?

---

### Post by frillybob on 2010-05-07
I fianaly solved my problems!


So here is what I did I made an ISO then booted it and right away I press f6 if not I get an error. Then I press f6 again and turn acpi off! I install it with dualboot. Then when I load windows 7 loades fine and to run Ubuntu 10.04 I have to press c for command line the type in acpi it should boot and that's it. I also have a vista installer which makes no sense but now I can dualboot!

---

### Post by ubunterooster on 2010-05-07
> **frillybob said:**
> I fianaly solved my problems!


So here is what I did I made an ISO then booted it and right away I press f6 if not I get an error. Then I press f6 again and turn acpi off! I install it with dualboot. Then when I load windows 7 loades fine and to run Ubuntu 10.04 I have to press c for command line the type in acpi it should boot and that's it. I also have a vista installer which makes no sense but now I can dualboot!
Wrong thread?

---

### Post by ubunterooster on 2010-05-07
> **frillybob said:**
> I fianaly solved my problems!


So here is what I did I made an ISO then booted it and right away I press f6 if not I get an error. Then I press f6 again and turn acpi off! I install it with dualboot. Then when I load windows 7 loades fine and to run Ubuntu 10.04 I have to press c for command line the type in acpi it should boot and that's it. I also have a vista installer which makes no sense but now I can dualboot!


[http://ubuntuforums.org/showthread.php?t=1474025&page=2](http://ubuntuforums.org/showthread.php?t=1474025&page=2)

^Thread that this post goes to

---

