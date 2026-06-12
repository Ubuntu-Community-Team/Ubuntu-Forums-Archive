---
title: "transmission torrent"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by this is new york not l.a. on 2009-05-10
ok so I was downloading a file earlier today using transmission and I haven't had a problem with it up until now. I downloaded the file and usually when its done there is a file on the desktop (or wherever you want to save it) and I'm on my merry way using the files. today however I finished downloading and there is no file. it has completely downloaded but I can't seem to find it anywhere. is there anybody that can help?

---

### Post by Didius Falco on 2009-05-10
Have you tried doing a search for the file?

 ```
sudo find / -type f -iname '*.jpg'
```

With the '*.jpg' replaced by whatever extension it is, or reversed, like 'batman.*'

That will search your whole partition...

I hope it helps...

Regards,

Didius

---

### Post by mprince on 2009-05-10
If the torrent is still listed in transmission you could highlight it and press the 'Details' button. Then click on the 'Info' tab and the 'Location: Data download' should be where the file is.

---

### Post by markbuntu on 2009-05-10
The default placement can be /home/user instead of /home/user/Desktop. This recently happened to me with a 4.4GB debian iso. I freaked out for a few minutes before I found it. You can also use the search function in the file manager.

---

### Post by joey-elijah on 2009-05-10
For future reference you may want to change Transmissions default download location to a 'downloads' folder perhaps?

---

### Post by this is new york not l.a. on 2009-05-10
didn't find anything but thanks for your guys help =/

I just save all the files I download to my desktop because thats the default setting then I can move them to wherever I want. looks like I have to download it again which sucks because its almost 2 gigs =[

---

