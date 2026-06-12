---
title: "Referring to brackets while manipulating files/folders etc..."
date: 2009-05-07
forum: New to Ubuntu
---

### Post by dE_logics on 2009-05-07
I searched for it :lolflag: there seems no way...or atleast no on has asked of how to refer brackets in terminal...or in that case in ANY cmd interface :lolflag:

Suppose I have a file/folder 'test(folder)' how do I refer to this in terminal?

---

### Post by mcduck on 2009-05-07
> **dE_logics said:**
> I searched for it :lolflag: there seems no way...or atleast no on has asked of how to refer brackets in terminal...or in that case in ANY cmd interface :lolflag:

Suppose I have a file/folder 'test(folder)' how do I refer to this in terminal?

You can use a backslash as escape character to strip any special meanings from the following character.

For example type the "test(folder)" as "test\(folder\)"

Still, the easiest way is to just use tab completion, as in type first characters of the file name and then hit tab key to automatically fill the rest.

edit: actually the best way is to avoid using special characters in file/directory names. ;)

---

### Post by dE_logics on 2009-05-07
Yeah...I was wondering that would happen...thanks anyway:)

---

