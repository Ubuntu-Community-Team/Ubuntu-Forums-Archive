---
title: "move list of files from server to ubuntu"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by snake_eyes on 2008-12-15
Hello,

I configured my Ubuntu as apache server, and I wanna transfer the site from X server to ubuntu.

I can download them by using the cURL command from the SSH and I know I can write such as this command:
```

 curl -O http://url.com/file.txt

```

and this if I wanna rename the second file
```

curl -O http://url.com/file.txt ftp://ftp.com/moo.exe -o moo.jpg

```

But is there a way to put all the my URLS from the old server in Txt file and then run a command to get them one by one?

Much appreciated in advance!

Cheers,

---

### Post by hyper_ch on 2008-12-15
why not just transfer them by rsync? or tar it and just scp that tar file?

---

### Post by snake_eyes on 2008-12-15
I have a directory its size is 2 GB and another one for the Attachments 3GB, so it's very easy to transfer them by set a list of urls that I need to be transfed in one file and then run the curl command.

Cheers,

---

