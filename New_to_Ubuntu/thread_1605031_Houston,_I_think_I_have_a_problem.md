---
title: "Houston, I think I have a problem"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by mikee55 on 2010-10-24
Hello, I don't know whats happening, I was trying to fix a sound card issue, Asus Xonar DS. And I now keep getting a red exclamation mark in a triangle, I click on it. Synaptic Package Manager opens and when I update I get this

W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg)  Could not resolve ‘archive.ubuntustudio.org’

W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_GB.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘archive.ubuntustudio.org’

W: Some index files failed to download, they have been ignored, or old ones used instead.


I'm using Karmic. Have broke it???

Mike

---

### Post by wojox on 2010-10-24
If you look at your link your using Fiesty archives, which don't even exist anymore.

```
http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg
```

---

### Post by GabrielYYZ on 2010-10-24
are those repositories? they don't look like the ones i'm used to (i.e. [https://launchpad.net/~tualatrix/+archive/ppa]("https://launchpad.net/%7Etualatrix/+archive/ppa") for ubuntu-tweak)

if they are, they might not be active anymore.

---

### Post by mikee55 on 2010-10-24
Thanks, but how do I rectify this?, Thank you

Mike

---

### Post by wojox on 2010-10-24
> **mikee55 said:**
> Thanks, but how do I rectify this?, Thank you

Mike

Edit your sources.list and change fiesty to karmic.

---

### Post by mikee55 on 2010-10-24
wojox, hi. How do I go about doing this, please?

Thank you

Mike

---

### Post by GabrielYYZ on 2010-10-24
hey mike, 

from the terminal (applications >accessories > terminal) type this 

```
sudo gedit /etc/apt/sources.list
```your password will be requested, enter it and then, find the 2 lines you mentioned in the OP and change feisty to karmic as wojox suggested.

---

### Post by mikee55 on 2010-10-25
Sorry for late reply, went to bed. I edited my sources list. Thank you for all your help.

Mike:)

---

### Post by mikee55 on 2010-10-25
How do I flag this as Solved?   :)

Mike

---

### Post by migs73 on 2010-10-25
> **mikee55 said:**
> How do I flag this as Solved?   :)

Mike
At the top of the first thread, there is a menu called thread tools, click on that and select 'mark as solved'.


:)

---

### Post by Verbeck on 2010-10-25
> **mikee55 said:**
> How do I flag this as Solved?   :)

Mike

the option is under **[COLOR=Red]thread tools[/COLOR]**. see the top

---

### Post by 3rdalbum on 2010-10-25
Please don't advise people to edit their sources.list manually - please advise them to use the Software Sources program, because it limits the problematic that they can accidentally create.

---

