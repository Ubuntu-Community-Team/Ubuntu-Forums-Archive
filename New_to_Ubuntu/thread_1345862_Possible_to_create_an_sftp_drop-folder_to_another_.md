---
title: "Possible to create an sftp drop-folder to another network?"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by tstack77 on 2009-12-04
I'm not even sure if the title makes sense, but I would like to be able to simply drag and drop a file from my computer and have it sent to my sister's computer a few miles away. Currently I am able to do this with an sftp client, but I would love to be able to streamline this procedure.

-axel

---

### Post by Excedio on 2009-12-04
What is it about sftp that is not streamlined?

---

### Post by tstack77 on 2009-12-04
Having to use an sftp client. I would like to be able to simply have it be a folder on my desktop that I can drop a file into, and to make it persistent so it's still there on a reboot.

---

### Post by Excedio on 2009-12-04
Places > Connect to Server
 
Select SSH and fill in the appropriate information. Be sure to check the box that says "Add as a bookmark."
 
From then on you will see that sftp listed in your Places dropdown. You will also be able to access from [COLOR=black]Nautilus[/COLOR] any time it's open.

---

### Post by tstack77 on 2009-12-04
Wow, THANKS. That was a whole lot easier than I thought it would be.

How would I go about doing this from the command line on my headless server to make a folder that I could simply cp files to in order to send on?

---

### Post by Excedio on 2009-12-04
Hmmm...sftp through command line it not really my thing. Maybe someone else can step in and provide some info?

---

### Post by tstack77 on 2009-12-04
Thanks for the help anyway, I just figured it would be great to have the ability from all my computers. I'll mark this as solved and ask that question in the server forum.

EDIT: anyone looking for a solution, google sshfs

---

### Post by Excedio on 2009-12-04
No problem...glad I was able to assist. :-)

---

