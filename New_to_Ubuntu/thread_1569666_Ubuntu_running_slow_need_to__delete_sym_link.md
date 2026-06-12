---
title: "Ubuntu running slow need to  delete sym link"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by mike101 on 2010-09-07
Hello

I'm new to Ubuntu. I've been having some trouble with my file system due to I think accidently creating a symlink (see below). I've been advised to delete it. But how do I do this. What exactly do I type into the terminal?   

ok this is what I  was looking for
 	Quote:
 	 	 		 			 				 					Originally Posted by **mike101** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9813438#post9813438") 				
 				*lrwxrwxrwx  1 mike mike       23  2010-09-06 18:13 Desktop -> /home/mike/Home/Desktop*
 			 		 	 	 
but the problem is that I didnt see that Home/ directory.
You should delete this symlink that is called Desktop and create a new  directory there named Desktop. Or renamed one of your backups to match  'Desktop'

 	Quote:
 	 	 		 			 				 					Originally Posted by **mike101** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9813438#post9813438") 				
 				[I]drwxr-xr-x  3 mike mike     4096  2010-09-04 09:14 DESKTOP 16TH AUGUST
drwxr-xr-x  3 mike mike     4096 2010-08-18 10:57 Desktop2[/I]
 			 		 	 	 

 		                   		  		  		 		 			 				__________________

---

