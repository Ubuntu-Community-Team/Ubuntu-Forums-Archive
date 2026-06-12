---
title: "Quick Nubie question"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by GOODY0 on 2010-02-10
I used the locate "app-name" command and found the location of the app I was looking for.  I deleted the directories and files that were listed in the locations.  I now have the following even though I deleted these folders/files:


  /simpana
/opt/simpana
/usr/bin/simpana
/usr/sbin/simpana


Any ideas on why they are still listed.  An ls shows nothing.

Thanks

---

### Post by capybara! on 2010-02-10
It is still indexed in a database. Try the command 'updatedb', then the locate command should show you only existing files.

---

### Post by GOODY0 on 2010-02-10
Thank you sir!  That did it

---

### Post by ubunterooster on 2010-02-10
Please click on thread tools then on "mark as solved". Thank-you

---

### Post by GOODY0 on 2010-02-11
ubunterooster - Thanks for pointing me in the right direction.  New to these boards.

---

### Post by ubunterooster on 2010-02-11
Glad to help, I've made that mistake myself. I was hoping I wasn't being to strong and appearing offensive. Nice to know no insult was taken and welcome to the forums

---

