---
title: "Trouble mounting a FTP server as a folder"
date: 2013-09-23
forum: Networking &amp; Wireless
---

### Post by fantomx11 on 2013-09-23
First let me state my goal. I want to have offsite synchronization, similar in functionality to dropbox.

My initial thought is to use an FTP server since I have one already set up and barely utilize it. I've installed curlftpfs, but when I try to connect it merely says "Error connecting to ftp:". I can connect to the server using the ftp command, but it gives the message "421 Sorry, cleartext sessions are not accepted on this server." So, it may be a problem with that. I've tried using the curlftpfs to mount ftp.kernal.org, which it does just fine. So I think the problem has to do with figuring out the right commands to connect to my server.

Now, that being said, if I can get that working great, but I'm also willing to entertain to other solutions to get to my primary goal which is the offsite synchronization.

---

### Post by The Cog on 2013-09-23
I would strongly recommend using SFTP rather than FTP. SFTP runs over SSH, and you probably want SSH access as well anyway.

If your objective is synchronisation, I would also suggest using rsync (rather than SFTP) because rsync can do file comparisons, and only transfers files (or even parts of files) that have changed. Rsync also runs over SSH. 

For a first step, try installing openssh-server on the server. make sure all your passwords are strong ones, and consider setting up passwordless (public key) authentication for it instead of using passwords. Then you can use ssh for remote command prompt (with X GUI tunnelling if you want) and you can use an sftp client for file transfer. For sftp clients, there is a command-line client  e.g. "sftp username@1.2.3.4" or nautilus (your normal file manager) can act as an SFTP graphical client.

---

### Post by fantomx11 on 2013-09-23
Well, I don't have access to install any software on the server since I merely pay the hosting company a fee to host it. If rsync can work only from my client computer, that could be a solution.

The server I have has FTPS available, but I cannot find anything on the host's website that says it has SFTP available.

---

