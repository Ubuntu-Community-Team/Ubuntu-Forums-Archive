---
title: "[SOLVED] OpenOffice updates are not authenticated on Update Manager"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-01-11
Yesterday, my Update Manager gave me a number of OpenOffice updates.

When I go to install the updates, it gives me the warning:

> Warning
You are about to install software that **can't be authenticated!** Doing this could allow a malicious individual to damage or take control of your system.
NOT AUTHENTICATED
openoffice.org-l10n-common
openoffice.org-l10n-en-gb
openoffice.org-help-en-gb
openoffice.org-help-en-us
openoffice.org-l10n-en-za
ttf-opensymbol
ure
uno-libs3
I have not installed these. Do you know what is going on and what I should do about it?

I'm using **Ubuntu 8.04 Hardy**, with **OpenOffice 3.0.0** installed.

Thanks

---

### Post by andresmh on 2009-01-11
You need to have a valid key for the repositories you're using. It is possible something happened on their end that invalidated their keys or maybe you removed the keys from your computer.

---

### Post by Paddy Landau on 2009-01-11
> **andresmh said:**
> You need to have a valid key for the repositories you're using. It is possible something happened on their end that invalidated their keys or maybe you removed the keys from your computer.
I've just noticed that there's a "Show Details" button, and it reveals that these are release candidates.
```
openoffice.org-help-en-gb (version 1:3.0.0-6ubuntu0hardy1) will be upgraded to version 1:3.0.1~rc1-2ubuntu1~hardy1
openoffice.org-help-en-us (version 1:3.0.0-6ubuntu0hardy1) will be upgraded to version 1:3.0.1~rc1-2ubuntu1~hardy1
openoffice.org-l10n-common (version 1:3.0.0-6ubuntu0hardy1) will be upgraded to version 1:3.0.1~rc1-2ubuntu1~hardy1
openoffice.org-l10n-en-gb (version 1:3.0.0-6ubuntu0hardy1) will be upgraded to version 1:3.0.1~rc1-2ubuntu1~hardy1
openoffice.org-l10n-en-za (version 1:3.0.0-6ubuntu0hardy1) will be upgraded to version 1:3.0.1~rc1-2ubuntu1~hardy1
ttf-opensymbol (version 1:3.0.0-6ubuntu0hardy1) will be upgraded to version 1:3.0.1~rc1-2ubuntu1~hardy1
uno-libs3 (version 1.4+OOo3.0.0-6ubuntu0hardy1) will be upgraded to version 1.4+OOo3.0.1~rc1-2ubuntu1~hardy1
ure (version 1.4+OOo3.0.0-6ubuntu0hardy1) will be upgraded to version 1.4+OOo3.0.1~rc1-2ubuntu1~hardy1
```If I understand correctly, release candidates are not stable releases.

If so, then it would explain why I don't have keys; at no stage have I requested non-stable releases. Well, to the best of my knowledge I haven't; perhaps I did so by accident.

Do you know what I can do to stop getting these release candidates (or have I misunderstood)?

---

### Post by Norm24 on 2009-01-11
When I installed 3.0 I had to add
```
http://ppa.launchpad.net/openoffice-pkgs/ununtu intrepid main
```
to System>Admin>Software Sources>Third-Party Software and have the box checked in order to receive updates.

But because 3.0 is not yet supported officially in Ubuntu,updates show as not being authenticated.

I've updated to 3.0.1 with no issues.The updates come straight from Sun.

---

### Post by Norm24 on 2009-01-11
> **Paddy Landau said:**
> If I understand correctly, release candidates are not stable releases.

If so, then it would explain why I don't have keys; at no stage have I requested non-stable releases. Well, to the best of my knowledge I haven't; perhaps I did so by accident.

Do you know what I can do to stop getting these release candidates (or have I misunderstood)?

Go to:
System>Admin>Software Sources>Third-Party Software and uncheck a line similar to this:
```
http://ppa.launchpad.net/openoffice-pkgs/ununtu intrepid main
```

You will no longer receive updates to 3.0

---

### Post by Paddy Landau on 2009-01-11
Thanks for the clarifications, Norm24.

My line reads:

[FONT=Courier New]http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main[/FONT]

Was I correct that RC1 means a non-stable release? As I use my machine for business, I want to stick with stable releases.

So, I'll untick the line and manually download stable updates when they become available.

---

### Post by Norm24 on 2009-01-11
> **Paddy Landau said:**
> Thanks for the clarifications, Norm24.

My line reads:

[FONT=Courier New]http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main[/FONT]

Was I correct that RC1 means a non-stable release? As I use my machine for business, I want to stick with stable releases.

So, I'll untick the line and manually download stable updates when they become available.

Release Candidates are considered "unstable".

In this case the only reason it shows as Unautheticated is because the software source is a 3rd party source.The source is reliable as far I'm concerned.

Once 3.0 is added to the Ubuntu repos all updates should be "authenticated".

I've been using 3.0.1 without any issues whatsoever.

---

### Post by Paddy Landau on 2009-01-11
Thanks, Norm24. I've unticked the box, which has removed the update request. I'll update OO manually from now on.

---

