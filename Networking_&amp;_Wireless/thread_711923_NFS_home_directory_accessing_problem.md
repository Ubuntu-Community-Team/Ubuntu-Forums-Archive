---
title: "NFS home directory accessing problem"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by rajul on 2008-03-01
I configured ubuntu 7.10 as nfs client, and used the nis user login. After login, my home directory mounts to the corresponding nfs folder. 

But I am not able to access folders or files inside Home directory. I am getting a pop-up error message - "The folder content could not be displayed." When I try to cd a directory in home through command prompt, it says "Not a directory" But ls -l  shows it as a directory as well as my user id as the owner of the directory. 

However I can access same folders with same login from other linux nfs clients(redhat and suse).    
Our NFS server has Tru64 Unix OS. and it is properly configured with other linux nfs clients.

I have gone through many posts on ubuntuforums related to this problem, but I found none as solving my problem. Please tell me what to do to resolve this problem.

---

### Post by rajul on 2008-03-02
I want to add one more thing that I am able to access some of the folder inside the nfs folder.

---

### Post by rajul on 2008-03-02
got temporary solution by changing version of nfs ( used by client) from 3 to 2

---

