---
title: "Ubuntu Randomly Logged Out?"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by Goveynetcom on 2010-03-09
I was listening to some music and browsing the net when suddenly with out warning my account logged out. Any reason for this to happen?

I have been using Ubuntu for a while now and this has never happened before. 

I don't think I accidentally clicked log out. My other thought is that I had a weird combination of buttons for logging me out...

Anyone else have had this problem?

---

### Post by earthpigg on 2010-03-09
this sounds like either X or GDM crashed, and restarted.

run this, and look for the time the problem happened:

sudo cat /var/log/errors.log

---

### Post by Goveynetcom on 2010-03-10
I went to the directory in terminal, and the file wasn't there. Leading me to believe I haven't had an error for that yet. So maybe I was just a random occurrence or my super sensitive touchpad making me click things on accident.

---

