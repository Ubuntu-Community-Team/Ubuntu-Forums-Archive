---
title: "Wine install changed my fonts?"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Tahakki on 2010-01-07
I installed wine, and now the fonts have changed, most noticeably in Firefox. How do I get them back to normal? As far as I know, the Microsoft fonts were already installed from the ubuntu-restricted-extras package.

Help?

---

### Post by marco123 on 2010-01-08
Delete the .fontconfig folder and the .fontconfig file in the /home directory then log out and back in and see if that helps.

They're hidden files so you'll need to Ctrl+H in your home directory to see them.

---

### Post by Tahakki on 2010-01-09
I solved the problem by using the stable version of wine.

Could it have been the wine-gecko package?

---

