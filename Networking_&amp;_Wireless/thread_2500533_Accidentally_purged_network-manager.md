---
title: "Accidentally purged network-manager"
date: 2024-09-04
forum: Networking &amp; Wireless
---

### Post by yaminb on 2024-09-04
So I booted my computer today and my wifi wasn't showing up. I'm not sure if it was an update or something.

I googled and it was early and the solution a few people showed was to apt purge network-manager and then install it again. I was silly and blindly did it, forgetting that would could it get it from the repo if wifi is not connect. I am not currently plugged into ethernet. In the worst case, I can connect if need be.

Is there anyway I can manually 'download' the required deb files for network-manager and then reinstall it. I have a windows partition that I can access to download the deb files and then put it on the ubuntu partition if needed.
I just don't know which ones to download.

I am on the latest Ubuntu 24.04 (up to date as of yesterday when everything was working)

---

### Post by yaminb on 2024-09-04
this post solved it:
[https://askubuntu.com/questions/652401/i-accidentally-deleted-the-network-manager-and-dont-have-access-to-internet-any](https://askubuntu.com/questions/652401/i-accidentally-deleted-the-network-manager-and-dont-have-access-to-internet-any)

and after reinstalling network-manager, my wifi was fine. Strange ordeal, but it's all good now.

---

