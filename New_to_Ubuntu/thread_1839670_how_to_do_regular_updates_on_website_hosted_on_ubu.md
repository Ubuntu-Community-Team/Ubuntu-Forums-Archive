---
title: "how to do regular updates on website hosted on ubuntu server"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by richyrage on 2011-09-06
Hello Ubuntu Community,

My current question lies within this realm.
I have asked and have been told that using openssh with putty is the way to 
go to access the ubuntu server remotely from another machine.thats cool.

But currently I have a machine that is used for working locally on my website using
dreamweaver, and there is the option to connect to local server (which would be the ubuntu test server at home), and I would like it to work on home machine, update to the ubuntu test server(also at home), and if all goes well to update on the server on my hosting site...(which wouuld be the remote site settting in dreamweaver)

Is this workflow safe, or would you recommend using some thing like bluefish to 
remotely update the production site? or how do you guys go about this process

Please share how u guys are goin about it, because I need a workflow that is safe, simple, and allows for constant updating (daily) for the production site to be optimal .

Thanks in advance,

RR

---

### Post by richyrage on 2011-09-06
bump

---

### Post by wolfgangmcq on 2011-09-06
I don't know much about Dreamweaver, but it sounds fine to me. What are you worried about?

---

### Post by bodhi.zazen on 2011-09-06
> **richyrage said:**
> Hello Ubuntu Community,

My current question lies within this realm.
I have asked and have been told that using openssh with putty is the way to 
go to access the ubuntu server remotely from another machine.thats cool.

But currently I have a machine that is used for working locally on my website using
dreamweaver, and there is the option to connect to local server (which would be the ubuntu test server at home), and I would like it to work on home machine, update to the ubuntu test server(also at home), and if all goes well to update on the server on my hosting site...(which wouuld be the remote site settting in dreamweaver)

Is this workflow safe, or would you recommend using some thing like bluefish to 
remotely update the production site? or how do you guys go about this process

Please share how u guys are goin about it, because I need a workflow that is safe, simple, and allows for constant updating (daily) for the production site to be optimal .

Thanks in advance,

RR

You can use Dreamweaver to update you home servers , but use ssh to update the production server.

If you need to transfer files use sftp or ssh (sshfs) or winscp.

---

