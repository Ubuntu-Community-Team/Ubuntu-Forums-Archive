---
title: "Cannot copy files from local to remote server via scp or sftp but can ssh"
date: 2014-11-01
forum: Networking &amp; Wireless
---

### Post by buntu_hugenewbie11 on 2014-11-01
So I have a very strange issue.
I can ftp files in windows using filezilla to remote server. 
But when I try to do it in Ubuntu (14.04) from the same machine I get an empty file created on the remote machine.
I can ssh to the machine from Ubuntu (but I did have to make some changes to make this happen: [https://nowhere.dk/articles/natty-narwhal-problems-connecting-to-servers-behind-cisco-firewalls-using-ssh](https://nowhere.dk/articles/natty-narwhal-problems-connecting-to-servers-behind-cisco-firewalls-using-ssh)).
I do have to vpn to get on the server network, but this is not an issue for ssh or for sftp in windows so I am not sure why it would be in linux.
But when I sftp or scp to the server, I enter my credential and in sftp it stalls and in scp it creates a blank file and stalls.
For scp the verbose output provides the following at the end:
```

sending command: scp -v <file>
Sending file modes: C0640 1051556 <file>
Sink C0640 1051556 <file>
<file>

```

And then it eventually stalls out.
Any ideas?
I end up having to go to windows to upload files to the server right now.

---

### Post by slickymaster on 2014-11-01
*Moved to the ***Networking & Wireless*** sub-forum*

---

