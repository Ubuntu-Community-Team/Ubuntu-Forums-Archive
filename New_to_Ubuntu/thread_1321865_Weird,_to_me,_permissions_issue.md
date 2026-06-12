---
title: "Weird, to me, permissions issue"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by knottshawk on 2009-11-10
One of my network adapters requires I use Wireshark as root in order for it to capture packets. After I finish and save the file, it is not available to anyone but root. So, if I do gksudo nautilus and change the permissions so that they're wide open, or if I chmod 777 on the file, I still can't modify it or move it using my regular login.

What am I doing wrong here?

---

### Post by Sarmacid on 2009-11-10
```
sudo chmod +r file
```should make the the file readable by anyone, so you can copy it, or you could also change ownership```
sudo chown username file
```

---

### Post by knottshawk on 2009-11-10
Isn't chmod 777 even more wide open than chmod +r? I'm not sure why gksudo nautilus, and using nautilus to change permissions and ownership doesn't work...

---

### Post by lavinog on 2009-11-10
deleted, misunderstood the issue.

---

### Post by konqueror7 on 2009-11-10
using 'chmod' will only change the file's permissions. use 'chown' instead and change it to your user...as @Sarmacid stated above in the command...

```
sudo chown knottshawk yourfile
```

---

### Post by knottshawk on 2009-11-10
Again though, why doesn't gksudo nautilus work if I change permissions and ownership? Am I confused?

---

### Post by alphaniner on 2009-11-10
chown is really the better way to go here, though I would use ```
chmod username\: file
``` to change group ownership as well.

Still, you're right about chmod.  I dunno about changing permissions through nautilus (never do it) but if you chmod 777 the file, your regular user should definitely have full control over it.  Maybe if you post full terminal output including before and after **ls -l** we can get to the bottom of this.

Edit: Another thing to consider is folder permissions.  If the file in question is anywhere under /root you won't be able to touch it unless you've modified the permissions of /root.

---

### Post by lavinog on 2009-11-10
> **knottshawk said:**
> Again though, why doesn't gksudo nautilus work if I change permissions and ownership? Am I confused?

You have a point.
I don't have a ubuntu machine to test this out at the moment.

Did any of the command line solutions work?
If not, then the problem is something else, like a lock file.

---

### Post by konqueror7 on 2009-11-10
> **knottshawk said:**
> Again though, why doesn't gksudo nautilus work if I change permissions and ownership? Am I confused?

i tried 'gksudo nautilus' and changing the owner of a test file it works for me... you could try adding your group as owner also and see if that works,
```
sudo chown <user>:<group> <file>
```

or try changing the whole directory where the file is to your ownership,
```
sudo chown -R <user> <directory>
```

---

### Post by knottshawk on 2009-11-10
Thanks for the help folks... I believe it's working properly. I think I just had a case where I never tried all the solutions in the right scenario. Sometimes it was in the root directory, sometimes I didn't change owner, etc.

You're all correct though and it seems to be doing fine now. Thanks for the help....

---

