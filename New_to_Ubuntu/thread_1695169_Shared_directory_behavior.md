---
title: "Shared directory behavior"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by john77eipe on 2011-02-25
Hi,

I have a folder that is set to one of my supplement group(say, dev). and I have made it group read/write/executable.

But when I create files in that folder they belong to my main group and they are not group-rwx. How will I make all files created have the same permissions and group of it's directory?

Also I found out that another user belonging to the group dev is able to delete and create files. But he couldn't execute or append. That's strange. Delete but not append !!!

---

### Post by john77eipe on 2011-02-25
Please let me know if I should elaborate it with an example.

---

### Post by Old *ix Geek on 2011-02-25
> **john77eipe said:**
> Please let me know if I should elaborate it with an example.Yes. Please post the output of:
```
ls -l
```
in the parent directory of the directory you're referring to.

In other words, if the directory you're talking about is called **something** and it's located under **/home/user/yourname**, please be in **/home/user/yourname** when you issue the **ls -l** command. We need to see the permissions and ownership info for **something**. Then **cd** to **something** and again issue **ls -l** and post its output (all of it).

---

### Post by john77eipe on 2011-02-26
$ ls -l | grep share
drwxrwxr-t  2 eipe dev       4096 2010-12-16 20:34 share

---

### Post by doas777 on 2011-02-26
try using setGID on the folder that holds the share, and in your samba Create Mask. 
setGID on a folder will cause all files created in the folder to be owned by the same ownergroup as the folder. on executable files, it will cause the execution to occur under the rights of the group.

[http://en.wikipedia.org/wiki/Setgid](http://en.wikipedia.org/wiki/Setgid)

you can enable SetGID on a folder with
```
chmod -R g+s <folderpath>
```use sudo if the user does not have write permissions on the folder.

for samba, if you are using  /etc/samba/smb.conf, the create mask should be 2776 for your permission set. the 2 enables setgid.

---

### Post by john77eipe on 2011-02-27
Thank you.

I'm not on an ubuntu system right now. But I'll check tomorrow.

Also I'm not using Samba. What is it used for?

---

### Post by doas777 on 2011-02-27
ahh, after rereading, don;t worry about samba. I was under the impression you wished to share the directory over your network. anyway, just makes the job all the easier.

also in terms of Deleting/creating, you might also want to look into the [sticky bit]("http://en.wikipedia.org/wiki/Sticky_bit"). it allows users to only delete files on which they are the user-owner, even if the user has the write privilege. 
```

sudo chmod +t <path to dir>

```

that way everyone has write based on their group membership in Dev, and can add to eachothers files, but they cannot rename or delete files without first taking ownership (if they are able).

---

### Post by Morbius1 on 2011-02-27
doas777. It could be that we are saying the same thing in a different way but the original requirement was:
> But when I create files in that folder they belong to my main group and  they are not group-rwx. How will I make all files created have the same  permissions and group of it's directory?If you originally created a directory that has "dev" as group then I would set the permissions on that directory such that every new file "inherits" the group:
```
sudo chmod 2775 /path-to-directory
```But there is a problem. When morbius adds a new file it will save with the correct group but with the wrong permissions:
> owner = morbius
group = dev
permissions = 644
All other members of the dev group can still only read but not write to the file. 

I beleive what needs to be done next is to change the default umask from 022 to 002 in /etc/profile. Then the file will save as 664 allowing other group-dev users the ability to edit the file.

It's also possible I misunderstood the requirement :)

---

### Post by john77eipe on 2011-02-27
Yes you guys are right.
setgid on a directory helps to make the group id inheritable to all the files under the directory. So 1 problem solved. :D

[quote]I beleive what needs to be done next is to change the default umask from 022 to 002 in /etc/profile.[quote]

But this would affect all files created by the user. I guess there is no way we could make it happen for a specific directory alone.

I think the default behavior of unix is weird. Consider 2 user's john and tom belonging to group dev. Now a folder is created with dev as the groupid and group permission set to rwx.

John creates a file inside. Surprisingly Tom can delete that file but not modify/execute it.

---

### Post by Morbius1 on 2011-02-27
> I beleive what needs to be done next is to change the default umask from 022 to 002 in /etc/profile.[quote]

But this would affect all files created by the user. I guess there is no  way we could make it happen for a specific directory alone.[/quote][COLOR=Blue]*EDIT: Even with a built in spell checker I still can't spell believe. *[/COLOR]

Yes and No.

If you set umask to 002 then any new file created anywhere will have permissions of 664. But outside of the folder that you did a chmod 2775 it will save as owner = group = morbius. No other group can edit the file.
> John creates a file inside. Surprisingly Tom can delete that file but not modify/execute it.     Yep, I suppose that is wierd. It's the difference in the meaning of permissions on a directory vs a file:

Write on a file means the ability to edit it's contents - to add or delete the content of the file.

Write on a directory , in a way, means the same thing. The ability to add to or delete from the contents of the directory - i.e., add or delete files and subdirectories from the contents of the parent directory.

---

### Post by doas777 on 2011-02-27
> **Morbius1 said:**
> [COLOR=Blue]*EDIT: Even with a built in spell checker I still can't spell believe. *[/COLOR]

<snip/>...

Write on a file means the ability to edit it's contents - to add or delete the content of the file.

Write on a directory , in a way, means the same thing. The ability to add to or delete from the contents of the directory - i.e., add or delete files and subdirectories from the contents of the parent directory.

@Morbius
I have the same problem with spelling that particular word. I can never spell 'definitely' correctly with out the aid of machines.

I think this is where the sticky bit comes in. sticky constrains delete and rename without constraining write rights. if a files is owned by morbius:dev, I could not delete it even if the group provides me rwS, but I can write to it. I could only delete/rename files owned by doas777:dev. granted there is nothing to stop me from writing over your file with 0Bytes of data,  but that's a different problem.

your right I missed the constraint on g+rwx but I was under the impression that that was because files were not automatically created under the correct group, and if that problem was gone, then the constraint was as well. sometimes I dont read the op as throughly as I should.

and lastly, glad to see your still around after my hiatus.

---

### Post by Morbius1 on 2011-02-27
> **doas777 said:**
> glad to see [COLOR=Blue]your[/COLOR] still around after my hiatus. Looks like we have something else in common - neither one of us ever uses [COLOR=Blue]you're[/COLOR] in the right context. :)

---

### Post by john77eipe on 2011-02-28
Thank you.

---

