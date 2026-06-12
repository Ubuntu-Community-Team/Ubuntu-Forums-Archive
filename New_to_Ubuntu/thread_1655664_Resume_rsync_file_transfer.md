---
title: "Resume rsync file transfer"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-12-29
I know that what I'm about to ask is easy for someone but I don't know what I'm doing I know it is something like

rsync -vrPHtz -e ssh host:/remote_path/* /local_path/

lets say i have the above in a script. no gui have to do this by hand

i need hard links, file permissions, undated file changes, compresstion, and recurse into directorie.
is their some kind of log so know if i need to rerun the script? also how do i rerun rsync with the resume?

---

### Post by lance bermudez on 2010-12-30
$ rsync  --delete -vcrHpEtzPe ssh sever@10.0.0.7:/home/server/500gb/samba /home/thiscomputer/ -p 22
Unexpected local arg: /home/thiscomputer/
If arg is a remote file/dir, prefix it with a colon (:).
rsync error: syntax or usage error (code 1) at main.c(1236) [Receiver=3.0.7]

I keep getting this so what i do wrong. I want to Synchronize a remote directory with a local directory and a local directory with a remote directory. but i seem to be unable to get just this one to work. Please help

---

### Post by lance bermudez on 2010-12-30
I can get it to work from computer to server but not server to computer?
rsync --delete -avcrHpEtRzP /home/thiscomputer/Documents -e "ssh server@10.0.0.7:/home/server/500gb/samba/ -p 9455" --log-file=/home/thiscomputer/rlog

---

### Post by lance bermudez on 2010-12-30
COMPUTER TO SERVER
rsync --delete -avcrHpEtRzP /home/thiscomputer/Documents -e "ssh sever@10.0.0.7:/home/sever/500gb/samba/ -p 1234" --log-file=/home/thiscomputer/rlog

SERVER TO COMPUTER
rsync -avcrHpEtRzP -e "ssh -p 1234" sever@10.0.0.7:/home/sever/500gb/samba/ /home/thiscomputer/ --log-file=/home/thiscomputer/rlog

did I forget anything? anyone know something easier to sync the folders on a server with no gui?

---

