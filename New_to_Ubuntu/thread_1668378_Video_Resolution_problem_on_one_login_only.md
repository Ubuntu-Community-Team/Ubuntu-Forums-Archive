---
title: "Video Resolution problem on one login only"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by Dave_in_MD on 2011-01-16
Good Morning, Brand new to Ubuntu, installed ver 10.10 although the about lists it as 11.04 Natty Narwhal on a dual boot with Vista.  The original account that was made at install will not allow me to change the resolution from 800 x 600 to 1024 X 1068 without the desktop being cut off at the bottom and right side, and will not allow repositioning or resizing the desktop, although the shrinkage appears to be of the correct order.  The 2 accounts that I made, Admin with administrator rights and Guest with user I was able to change without any issue.  I also changed the original account from custom privileges to administrator with the same results.  I have checked all of the few places that I know how to check and have matched the settings and the original account still will not allow me to change it correectly.  An interesting anomaly is that when the screen shrinks when I do set it, the focus of the mouse position is where the accept button would be if the screen had not been resized as I can highlight the choice by moving the mouse in the black field.  I am reasonably sure that while looking around the first 2 days I must have made a change that I am not aware of on this account. 
as suggested on the getting started here is the terminal output: dave@dave-Train-DE051:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
While I could likely circumvent the issue by making another account, I would like to understand the issue and repair it.
Thanks in advance,
Regards,
Dave

---

### Post by robsoles on 2011-01-17
Hi Dave, Welcome to UF.

I can't remember the name of the per user X11 config file but if it is fixing you to 800x600 on the original account then by logging into the original (leave it, painful as it is, at 800x600 for this session) and using grep in terminal to search:

```
grep -R 800 * >> ~/Documents/find-800.txt
gedit ~/Documents/find-800.txt 
```The name of the file and a little of the content is listed for each hit in text files, go through them and see if you can identify one (it probably has xorg in it's name or at least starts with x) that you feel sure is your culprit then move it 'out of the way' and try logging out and back in again as that user

```
mv thisfile disabled-thisfile
```If it doesn't make a difference to ability to set display as desired then open terminal and move it back, look for another.

Please post the file full of output from that grep command I gave you if you can't seem to find your culprit.

---

### Post by Dave_in_MD on 2011-01-17
Thanks robsoles for the reply, I was beginning to think I violated a rule or really broke the system with no replies.

here is the output that you requested; 
Binary file Downloads/ubuntupocketguide-v1-1.zip matches
Binary file Downloads/ubuntupocketguide-v1-1.pdf matches

The above is the guide that I downloaded in trying to find the issue myself
Regards,
Dave

By the way, I have an Aunt that lives in NSW

---

### Post by robsoles on 2011-01-17
I hope your Aunt is high and dry without having made a great deal of effort to be so.

OK, so no text files matched and I expect it is being set in plain text so perhaps they are using a hexadecimal mode number instead of resolution size.

Look in ~/.config, you can use nautilus or terminal- in nautilus press [CTRL]+[H] to reveal hidden files if not already on display, in terminal:```
cd ~/.config
ls -al

cat monitors.xml
```
'ls -al' returns all files and folders hidden or not, I include 'cat monitors.xml' in that code box above - 'cat' will display the contents of the file named.

If the copy of ~/.config/monitors.xml doesn't match the one at /home/admin/.config/monitors.xml then replace it with admin's version of the file.

Keep poking through files, try other hidden folders and files in this user's home directory - every time one of us posts this thread it gets bumped to the top and someone who knows the name of the file (or list of names culprits might go by) might see the thread and let us know before we find it.

You did not violate any rule I know of, your original post is a fairly big continuous block of text and that doesn't encourage everybody to try to read through it to try to provide assistance.

---

### Post by Dave_in_MD on 2011-01-19
Sorry I couldn't get back to you, but with the ice storms, my satellite Internet was at a craw of about 1KBs yesterday. Your commands did indeed return resolution information, thank you.  I am going to put this on the side for now until I learn more about using the CLI and can understand the commands that I am running.
Thanks for your support.
Dave

---

