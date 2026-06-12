---
title: "software center wont open in 11.04"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by tj.welsh on 2011-08-02
recently re-installed Ubuntu 11.04 and have discovered that software center won't open. clicking it causes the icon to flash but nothing further.

when i run software-center in terminal i get this error:

Traceback (most recent call last):
  File "/usr/bin/software-center", line 111, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 52, in <module>
    from view.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/view/installedpane.py", line 33, in <module>
    from appview import AppView, AppStore, AppViewFilter
  File "/usr/share/software-center/softwarecenter/view/appview.py", line 42, in <module>
    from softwarecenter.models.appstore import AppStore
  File "/usr/share/software-center/softwarecenter/models/appstore.py", line 33, in <module>
    from softwarecenter.db.reviews import get_review_loader
  File "/usr/share/software-center/softwarecenter/db/reviews.py", line 38, in <module>
    from softwarecenter.backend.rnrclient import RatingsAndReviewsAPI, ReviewDetails
  File "/usr/share/software-center/softwarecenter/backend/rnrclient.py", line 32, in <module>
    SERVER_ROOT=distro.REVIEWS_SERVER
AttributeError: 'Debian' object has no attribute 'REVIEWS_SERVER'

---

### Post by computerandu on 2011-08-02
Try uninstalling and then re-installing it..

sudo apt-get remove software-center

sudo apt-get install software-center

---

