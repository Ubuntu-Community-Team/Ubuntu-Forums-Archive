---
title: "What's a good DIY Dropbox you can run from your own server?"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by diablo75 on 2011-07-03
I like to use Dropbox on my machines because it works on all sorts of platforms (from Windows, Mac and Linux to my cell phone) and automatically syncs files that change right after they're changed.  But I'm always on the border of running out of free space.  I would LOVE to be able to have a magic folder like this that's not limited in space and also have the ability to share folders with others, or even public links with others.  Any suggestions?

---

### Post by frankbooth on 2011-07-03
I have no idea if there are ready-to-use scripts or applications that you can use, but here's an idea...

You could make a bash-script that uploads the content of the folder to the server, here's some pseudo code:
```

#!/bin/bash
ftp IP USR:PAS ~/sync/ /ftp/upload/sync/

```

then use cron for scheduled uploads (eg: every 15th min) to keep the files synced.

But... This probably wouldn't do the trick for your Winsnooze machine ;), might also not be an optimal solution for your phone.

The easiest solution is of course to buy more space at Dropbox and support their awesome product. 
I'm loving it myself but have yet to run out of space.

---

