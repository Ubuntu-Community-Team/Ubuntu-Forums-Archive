---
title: "Why can't I see my Ubuntu shared folders on the network"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by jeffreyclong on 2008-11-25
Why can't I see my Ubuntu 8.10 shared folders and computers on a network with Samba installed and started and the folders shared.

I am a Linux newbie. I am running Ubuntu 8.10 and trying to share folders.

I believe I have properly set up Samba by right clicking on a folder, clicking sharing options, clicking "Share this folder" and "guest access" in the file manager>folder sharing window that opens. The first time I did this I got an error that the windows file system wasn't installed. I installed that. The second time I got another error that told me to add "usershare owner only = false"' to /etc/samba/smb.conf which I did by running sudo gedit. I restarted and was successfully able to share the folder.

However, the two ubuntu machines plugged into the network, both with folders shared following these procedures cannot see each other or these shared folders in the network file browser. I have successfully pinged both from each other so I know that they are both on the network. I am however able to see windows machines plugged into the network, just not the Ubuntu/Linux machines.

What am I doing wrong?

Thanks for any help you can provide

---

