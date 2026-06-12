---
title: "Disconnecting from a SSH session while a forwarded program is running"
date: 2015-01-01
forum: Networking &amp; Wireless
---

### Post by cody1233 on 2015-01-01
Hello, everybody!

I recently set up a server at my house and I am trying to convert a lot of videos using winff.  I have a laptop connected and am tunnelling X11 connections via SSH to get it running, but I want to shut the laptop down.  Is there a way to disconnect from the server and keep the program running?

Thanks in advance!

---

### Post by SeijiSensei on 2015-01-01
If you can use ffmpeg or avconv from the command line, you can put the process into the "background" by appending an ampersand to the end of the command.

```
ffmpeg ... &
```

It's a lot harder to do this with GUI programs, I suspect.

---

### Post by cody1233 on 2015-01-01
I was hoping I could avoid using these programs from the CLI, but it is looking like I will have to.  Thanks for your post!

---

