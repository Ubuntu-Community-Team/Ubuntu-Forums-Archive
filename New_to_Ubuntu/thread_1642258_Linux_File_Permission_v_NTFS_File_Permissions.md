---
title: "Linux File Permission v NTFS File Permissions"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by AlistairH on 2010-12-10
I'm looking for guidance on best/standard practices when implementing file permissions in Ubuntu Server 10.04 for a number of people.

I'm currently in the process of replacing a failed MS SBS 4.5 machine with one running Ubuntu Server 10.04 for a client.

On the SBS machine, in order to keep things simple for users, there was one main share point that contained folders for all the various documentation created by the staff. NTFS file permissions were used to restrict access on a group basis such that any one particular folder may have full access rights to GroupA, read only rights to GroupB while GroupC may be able to read  and write but not delete anything from the folder.

I'm unclear whether this level of control can be achieved via Linux file permissions.

The users will be running Windows XP/7 on their desktops so Samba will be serving up the shares that they see.

If anyone has links to further reading material that would discuss what is considered best practice in such an environment would be welcome.

Thanks in advance

---

### Post by Gone fishing on 2010-12-10
It certainly is possible to give user and group rights in Ubuntu or Linux in general. You can also setup access permissions in samba for windows shares etc.

I have on my server directories that only individuals can access, students can access but can't write to but teachers can write to, directories that admin can write to, teachers can read and students can't access at all etc.

I would consider using ldap as a backend for samba you could then easily integrate Linux clients using ldap authentication on the clients (like a Windows domain) samba recommends this anyway. I would also look at Webmin (just to make life easier)

---

### Post by AlistairH on 2010-12-13
Thanks for the reply Gone Fishing and apologies for taking so long to get back to you.

My understanding of Linux/Samba permissions is that I'd need to set up a number of different shares rather than the one share where the access rights for each individual subfolder/file are fine tuned through NTFS as was the case before on the client's failed MS server.

The client is moving much of their operations to the 'cloud' and the Linux file server I'm setting up is purely to hold existing data files that will not be uploaded to the cloud solution.

Through their now defunct MS SBS box, they were used to single sign on, so ideally the Samba server will provide the same functionality though I was intended to set it up as a PDC rather than go the LDAP route - partly because I'm unfamiliar with that and I do not have the time to invest to get up to speed for this particular requirement. All the client PCs are Win XP/Win 7 based anyway. I couldn't convince them to go open source.

While implementing a Linux based file server, I wanted to take the opportunity of tidying up the whole directory organisation which has, over time, been somewhat abused on the MS SBS server. What I want to do is implement standard Linux practices while minimising the differences that users will see compared to the old system.

---

