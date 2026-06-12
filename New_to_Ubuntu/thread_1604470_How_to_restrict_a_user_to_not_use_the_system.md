---
title: "How to restrict a user to not use the system"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by karthick87 on 2010-10-24
I want to restrict a user to not use the system more than 30 minutes..Is it possible with bash script or is there any package that will do this...?Like after 30 minutes the system should be locked and prompt for a master password to gain access to the system again..

---

### Post by Paqman on 2010-10-24
I believe Gnome Nanny can restrict how long a user can spend on the system. The package name is nanny, it's in the Universe repo on Maverick.

---

### Post by HermanAB on 2010-10-24
You could set it with PAM Session (easy), or RADIUS (if you are an ISP).

---

### Post by karthick87 on 2010-10-24
> **HermanAB said:**
> You could set it with PAM Session (easy), or RADIUS (if you are an ISP).

Can you give more information..?

---

### Post by .nedberg on 2010-10-24
You could also have a look at timekpr, see link in my signature!

You will find a PPA here: [https://launchpad.net/~timekpr-maintainers/+archive/ppa](https://launchpad.net/~timekpr-maintainers/+archive/ppa)

---

### Post by karthick87 on 2010-10-25
Thank you..!

---

