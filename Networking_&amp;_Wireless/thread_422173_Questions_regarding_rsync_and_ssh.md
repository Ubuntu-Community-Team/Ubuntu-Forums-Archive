---
title: "Questions regarding rsync and ssh"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by himurakenshin on 2007-04-24
I wanted to know, how does rsync transfer files (from one computer to another, not local directory mirroring)? I read that it uses SSH, but is SSH a file transfer protocol? and if so, is it file system dependent? I understand that FTP is file system independent, as it transfers the binary characters over (in binary mode), so the file system should not matter, and that FTP is faster than using SMB. I'm a bit confused as to how SSH would work, I use it currently for remote terminal access. Is a SSH daemon required for rsync to run? I am also aware that there is SFTP, using FTP over SSH or something like that, which confuses me even more. I would really appreciate an answer. Thanks a lot.

---

### Post by amniarix on 2007-04-25
> **himurakenshin said:**
> I wanted to know, how does rsync transfer files (from one computer to another, not local directory mirroring)? I read that it uses SSH, but is SSH a file transfer protocol? and if so, is it file system dependent? I understand that FTP is file system independent, as it transfers the binary characters over (in binary mode), so the file system should not matter, and that FTP is faster than using SMB. I'm a bit confused as to how SSH would work, I use it currently for remote terminal access. Is a SSH daemon required for rsync to run? I am also aware that there is SFTP, using FTP over SSH or something like that, which confuses me even more. I would really appreciate an answer. Thanks a lot.


SSH creates an encrypted tunnel for sending bits across. It doesn't specify what those bits are, so you can run any protocol you like over SSL - HTTP (https), FTP (SFTP), rsync, etc. The key thing to realise is that network protocols are layered: HTTP over SSL over TCP over IP. Lower layers don't know or care what upper layers are doing.

If you do a large rsync over SSH and run 'ps axwwwwu | grep ssh', you'll see that SSH process that your local rsync spawned:

ssh 192.168.0.146 rsync --server -logDtpr . 192.168.0.146

So the local rsync invokes 'rsync -server' over the SSH connection, and talks to it.

---

### Post by himurakenshin on 2007-04-25
so rsync is the transfer protocol ? is this file system dependant? and does that mean that an ssh daemon has to be running on the server to run rsync?

thank you very much for your reply

---

### Post by himurakenshin on 2007-04-27
bump

---

### Post by spd106 on 2007-04-27
Rsync is a transfer protocol, afaik it is file system independent/transparent.

Rsync doesn't do encryption which is one reason why ssh is used to tunnel it, you may also see it used when there isn't an rsync server listening. In this case ssh is used to set up a tunnel then spawn a new rsync daemon to initiate transfer with. The man pages explain it far better than I can.

You don't need ssh to be running if you have an rsync daemon listening on a port ready to accept connections. There are a few ubuntu rsync mirrors listed on the mirrors page in the wiki.

---

### Post by himurakenshin on 2007-04-27
thanks alot, I was wondering if there is any speed comparison between rsync, smb and ftp?

---

### Post by spd106 on 2007-04-28
Generally rsync is used to maintain file replication across sites such as mirror servers or backups because it only transfers file changes. This means it's not really geared up to maximise throughput, so it doesn't really compare with smb or ftp.

If you are starting from scratch then I believe ftp > smb >> rsync

If you already have a close match on both ends and just want the changes then rsync >>> ftp > smb

There is a sliding scale where you achieve ever decreasing benefits from rsync as the file difference increases. I have not done any scientific testing this is based purely on my experiences.

---

