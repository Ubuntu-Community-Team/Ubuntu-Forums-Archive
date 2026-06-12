---
title: "Samba Sharing Permissions Problem"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by dmaxel on 2009-04-29
OK, I'm having a few problems with my Samba configuration. There are two main problems.

Alright, I have two drives that I partitioned to be both ext3. We installed Samba server using the Sharing Options --> Share --> Install SAMBA prompt method, and then did the Sharing Options --> Share to actually share it. We put a folder in the drive that would hold everything, as sharing the drive was harder than just sharing the big folder inside the drive.
Things worked pretty smoothly until we came into more permissions problems. Here is the point where my problem/questions begin. We have set it Sharing Options so that the folder is shared and that people added to SAMBA through the sudo smbpasswd -a USERNAME method can read/write. No allowing guests. So it says that the entire folder belongs to the one username, on our machine called "server". The "server" username is the only normal user that has everything running. All other normal user accounts are just for Windows machines to get on, as those accounts get added to SAMBA.
So when I make a folder, everything goes OK. I can do whatever I want with it. However, when a family member tries to do something with that folder with their own SAMBA account, they aren't allowed to write into the folder. They have to make their own folder in the main share area if they want to write something. Therefore, we cannot put things into each other's folders that are inside the share area unless either the folder is made over VNC using the "server" username and that no folders are made inside of THAT folder, or if I change the permissions on the folders I make as long as I access them with Vista.
Simply said, I do not want to do that every time!!! I want to be able to make a folder on my Windows machine, and then be able to do anything and everything on every Windows machine in the household, without having to manually change permissions every time.
How can I make it that it automatically belongs to the "server" username, so that everyone who has access can also read and write? And if that doesn't work, what will?

OK, so that's the first scenario. After running into that problem, I decided to try to partition one of the two drives from ext3 to fat32. I thought, "Hey, maybe this will change the permissions to our advantage." In the end, it did change the permissions, but actually for the worse. Now whenever I try to make a folder in the drive and then share that folder, the share shows up on Windows machines, but when we try to access them, it says "access path not found". What could I do to fix this if fat32 is the way to go, or the above situation cannot be fixed?

Thanks a bunch for this help! I am still an Ubuntu newbie, so please be gentle. :popcorn:

---

### Post by dmaxel on 2009-04-29
Could anyone help?

---

### Post by dmaxel on 2009-04-30
Can anyone please help?

---

### Post by Miljet on 2009-04-30
I don't mean to be unkind but I have read you original post three times and still have no idea of what you are trying to do. That is probably why you haven't gotten any replies.

I would suggest that you re-think your original post and try to re-word it to better explain your situation.

For example:
1 - How many computers are you talking about?
2 - How are they connected?
3 - What operating systems are they using?
4 - Exactly what have you done so far? 
    > Sharing Options --> Share --> Install SAMBA prompt method
    I have no idea what this means.
5 - What errors are you getting and at what point are you getting them?
And so forth.

I am sure that someone will be glad to help you when they underatand what you are attempting.

---

### Post by dmaxel on 2009-05-01
> **Miljet said:**
> I don't mean to be unkind but I have read you original post three times and still have no idea of what you are trying to do. That is probably why you haven't gotten any replies.

I would suggest that you re-think your original post and try to re-word it to better explain your situation.

For example:
1 - How many computers are you talking about?
2 - How are they connected?
3 - What operating systems are they using?
4 - Exactly what have you done so far? 
    
    I have no idea what this means.
5 - What errors are you getting and at what point are you getting them?
And so forth.

I am sure that someone will be glad to help you when they underatand what you are attempting.
OK, I want to have all Windows computers in our network to be able to connect to the server, currently with only two samba accounts. They are connected over a router, both ethernet and wireless. I have tried to share a drive, as we are trying to make the server machine that is running Ubuntu 8.10 Desktop Edition into a....well, home server. Sharing the drive didn't work so well along with automatic mount settings, so we created one single folder inside the drive, named it, and shared the folder.

What I want to do is to be able to create a folder using one samba account, and have someone with a different samba account be able to create folders and place files into all folders, including those that I make. However, as soon as I create the folder, it officially belongs to me even on the server, and all other samba accounts are unable to place files into the folder that I created. And that's the problem. Folders that are made over the server itself under the control of VNC are fine, as anyone can do what they please with the **files** inside that folder because they officially belong to the server.

BTW, when I say it belongs to me, the server, etc, I mean what it says when I do right click --> Properties --> Permissions, and then what it says next to the owner label.

Is that better? If not, please tell me which part(s) I need to emphasize on. Thanks for trying to understand at least.

---

### Post by dmaxel on 2010-01-07
OK, now revisiting this after a couple of months...to keep it simple, here was the problem:

I share a folder, and give access to multiple users.
User A comes in and adds some files and makes some folders.
User B comes in after User A is finished and tries to place files in folders that User A made, but seems to not have permission to do so. Nor is User B able to change files placed by User A, but just able to read them.

Based on the problem above (and some research later on), would it have helped to add:
```
directory mask=xxxx
create mask=xxxx
```...into the samba config file to make it so that User B can add files into folders made by User A and so forth?

---

