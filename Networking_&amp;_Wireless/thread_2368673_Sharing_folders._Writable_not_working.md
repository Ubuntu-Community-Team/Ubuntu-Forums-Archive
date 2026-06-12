---
title: "Sharing folders. Writable not working?"
date: 2017-08-13
forum: Networking &amp; Wireless
---

### Post by kiicki on 2017-08-13
I just fresh installed Ubuntu 14.0.3 and everything is up to date. I choose this version because it is the latest version that still supports my GPU, and it worked a lot better than the open source.

About 2-3 months ago I shared my folders where they were all writable, at least what I remember but that doesn't work anymore. I have tried the "local sharing" and I have tried "Samba" where I want to share my "Downloads" folder but with Samba, it's not writable. I'm pretty sure it was before. With the stock "local sharing" the downloads folder is indeed writable, but folders inside "downloads" are not writable.

As an example I have a "downloads" folder that contains 2 other folder named "movies" and "tv-shows". When I share "downloads" it only makes "downloads" writable, but not movies and tv-shows. i want everything to be writable so I don't have to individually share each folder and select "writable". If I share and make downloads writable, I want everything in that folder to be writable.

The shared folders on Ubuntu will be mapped to another computer that runs Windows 10. From my windows 10, I would like to be able to edit and add content to my shared writable folders. Is there a way to make the "downloads" folder writable and everything in it?

What I can tell is with Samba, nothing is writable even when I select writable. With the stock "local sharing" only the folder I shared is writable. not the folders that is inside that shared folder, evne though they are actually readable. Problem is that they are not writable.

---

### Post by Morbius1 on 2017-08-14
Given your description the easiest way to do this is:

** Edit /etc/samba/smb.conf
** Find the line[B] workgroup = WORKGROUP
[/B]** Right under it add this line:
```
force user = morbius
```
[COLOR=#0000cd]*Change morbius to your Ubuntu login user name*[/COLOR]

** Save the file and restart smbd:
```
sudo service smbd restart
```

Now everything that the client user does to your samba shares will be as you.

---

