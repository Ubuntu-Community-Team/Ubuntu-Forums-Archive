---
title: "CVS: why &quot;DO NOT EDIT FILES IN THE REPOSITORY!&quot;"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by flylehe on 2009-03-19
Hi,
I am new to CVS. So please excuse me for possibly not being clear about things.

I'd like to use CVS to exchange my programming files between my computer and a server where my CVS repository will be. I heard that "DO NOT EDIT FILES IN THE REPOSITORY!" but not quite understand. Are the code files in the repository just for back-up storage and version records and should not be edited directly and not be compiled and run? 

Here is what I think now. Most of the time I will do coding on my computer, add to the repository and run them from there on the server. However sometimes I also like to edit my code on the server and run it, because my computer and the server have different systems and packages installed. Does this mean that I will directly edit files in the CVS repository or I will have two copies of my files in the server: one for repository and one for my editing, between which I also need to cvs add and checkout?

Thanks in advance!

---

### Post by cwsnyder on 2009-03-19
I know **A** reason why you should not edit the files in the repository.  Unless you are the ONLY person using said repository, and all other users are locked out at all times, someone ELSE may be updating or attempting to update against the repository!

Edit files and trials should only be done on an isolated server without a repository or on workstation files.  Strictly speaking, such a 'server' is not a server at all!  It is just another workstation which you can control from your console.

Sandbox such trials.  Crashes should only affect you, not other users.  If you actually have a server which is in use, you CAN AND WILL crash said server in attempting to do what you describe.

---

### Post by lovinglinux on 2009-03-19
I will give you an example how I work with Firefox extension development and svn. 

I don't use a server, so I keep everything on the same machine. I have the svn repository in a special folder, the files I'm coding on a workspace folder (which include the hidden .svn folders and files) and an exported copy on the extension folder (which have only the program files).

So I edit the files in the workspace only. When I need to test the changes I do a directory diff between the workspace and the extension folder, without sending the hidden files. Then I run the code in the extension directory. If I'm satisfied with the result, then I commit the changes from the workspace to the svn repository. I never edit the files in the repository, because this would mess with the versioning system. Sometimes I edit the files in the extension folder, but then I have to do a diff back to the workspace, because is not possible to commit the changes from the extension folder, since it only has the program files.

If something goes really bad, all I have to do is to delete the workspace folder entirely and checkout the files from the repository to the workspace again. When I need to release a new version, I just export from the repository. Checkout includes the hidden versioning files while export includes only the final product.

In you case you could have the repository on your server, a workspace on the local machine and a workspace on the server. If you like to edit files on the server, then do a checkout from the repository on the server to the server workspace and edit from there. When you finish you can commit the changes to the server repository. Is like if you are working with another developer who uses the server to edit the files and while you use the local machine. Both commit files to the repository on the server, but you never edit the files in the repository directly.

---

### Post by flylehe on 2009-03-19
Thanks!
To cwsnyder:
Yes, I am intended to be the only user. What is the difference between a workstation and a server? What does "Sandbox such trials" mean? 
To lovinglinux:
What is the extension folder used for? Can't you run your code in your workspace directory?
How do you do a directory diff between the workspace and the extension folder? I think "diff" only can compare two files?

---

### Post by lovinglinux on 2009-03-19
> **flylehe said:**
> To lovinglinux:
What is the extension folder used for? Can't you run your code in your workspace directory?
How do you do a directory diff between the workspace and the extension folder? I think "diff" only can compare two files?

I could run the code from the workspace if I create a symlink to the extension directory, because this is the place where Firefox looks for extension files. But this is a particular case of FF extension development. You could run a program in C++ from the workspace if you want for example.

I like to work this way, because the workspace contains the versioning files and folders, while the extension directory contains only the code. I can commit from the workspace but not from extension directory.

Directory comparison can be done using Meld. It's in the repositories and it is a great diff application.

---

### Post by cwsnyder on 2009-03-20
> **flylehe said:**
> Thanks!
To cwsnyder:
Yes, I am intended to be the only user. What is the difference between a workstation and a server? What does "Sandbox such trials" mean? 
The major difference intended between a server and a workstation is a server is intended to share or host resources for use by another user or group--a workstation is intended to work with resources provided internally or by server(s) in a network.  The line is blurred when you run a peer-to-peer network (like SAMBA, or bit-torrent), but you will find the distinction embedded in GNU/Linux (and UNIX) with the X-terminal server and client software and others.  Examples of servers are file-servers (remote storage on a network), print-servers (provide a shared printer to designated groups on a network), web-servers (host an Internet web page or pages), and even media-servers (providing a central repository for digital videos and music for sharing over a network.

'Sandbox'-ing is the procedure where you limit the damage which can be caused by a rogue application which may break and cause your computer to freeze or even cause a kernel panic which will make you restart your computer.

---

