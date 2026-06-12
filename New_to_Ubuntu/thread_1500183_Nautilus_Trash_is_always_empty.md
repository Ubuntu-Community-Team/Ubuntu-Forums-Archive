---
title: "Nautilus Trash is always empty"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by const451 on 2010-06-02
I am using Ubuntu Lucid and Nautilus Trash is always empty. I accidently deleted a file, to restore it I went to Trash but it was empty.

Is Trash not working or I have to set some setting?

THX

---

### Post by Cathhsmom on 2010-06-02
If you hit delete, it deletes permanently.  But if you right click the file and say move to trash, it will be there to restore if necessary.  But if you empty the trash, it permanently deletes the file(s).

---

### Post by Ozymandias_117 on 2010-06-02
I would go to gconf-editor and go to apps/nautilus/preferences/enable_delete and make sure it isn't checked so you send stuff to the trash.

---

### Post by const451 on 2010-06-02
I see, thank you! I still have questions:

1. How to program Delete button to send files to Trash instead of permanently deleting them?

2. It is not possible to sort files in Trash by date of deletion?

---

### Post by const451 on 2010-06-02
> **Ozymandias_117 said:**
> I would go to gconf-editor and go to apps/nautilus/preferences/enable_delete and make sure it isn't checked so you send stuff to the trash.

I  see - thank you!

---

### Post by Ozymandias_117 on 2010-06-02
Right click in the Trash and select "Arrange items" and select "Modification Date"

---

### Post by const451 on 2010-06-02
So a 'date modified' in Trash is the date a file was deleted ?

---

### Post by Ozymandias_117 on 2010-06-02
Pretty sure, let me test it really quick.

---

### Post by Ozymandias_117 on 2010-06-02
Oops, I guess it doesn't. Sorry, my fault.

---

### Post by const451 on 2010-06-03
alright, thank you.

---

