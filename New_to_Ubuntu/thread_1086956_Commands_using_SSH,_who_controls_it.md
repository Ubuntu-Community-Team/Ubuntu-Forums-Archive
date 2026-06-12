---
title: "Commands using SSH, who controls it?"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Jevans91 on 2009-03-04
Hi there,
-Preamble-
I currently have set up Ubuntu desktop, which connects via SSH to a headless Ubuntu server and am moving some pretty large files about using 'cp' and as there is no progress bar just left it, and was wondering:
-End Preamble-

If I run cp <File> <Destination> over SSH and then close the Terminal (Severing the SSH connection?), will the cp command stop, or continue on like nothing happened because the process is running on the Server PC?

Well, I hope that was understood, was just a question I had in the back of my mind so thanks for your insight!

---

### Post by Locke_99GS on 2009-03-04
I'm unsure if, but doubt that, it will continue once you sever the SSH connection.

You CAN, however, start a *screen* session within the SSH session, and it will live on after you close the SSH connection. You can even hop back into it when you come back.

See *man screen*.

---

### Post by RetchingRabbit on 2009-03-04
Other possibility is to do ```
cp source target &
```That should background the process, and I believe that will allow you to terminate the ssh session.

---

### Post by The Cog on 2009-03-04
> **RetchingRabbit said:**
> Other possibility is to do ```
cp source target &
```That should background the process, and I believe that will allow you to terminate the ssh session.

I don't think that will help - it will still die if teh SSH disconnects. Solutions I can think of are:
```
nohup cp source dest &
```
or
```
cp source dest &
disown
```
Or use **screen** as Locke_99GS suggested. Screen is worth getting to know. Google for tutorials cos it's a bit cryptic.

---

