---
title: "clear create document list"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by klein de usa on 2011-02-08
hi 
i have been trying to clear the create document list and can not find a way. **_if you right click on your desk top and go to create document_** a list appears of all the recent documents you have had open. how do you clear this list? where is the file it is reading and how do you disable it?

---

### Post by aeiah on 2011-02-08
if its the same recent documents list that you can find in your menu (in places, i think), then you can clear them from there

---

### Post by mcduck on 2011-02-08
I have no idea how the "Create Document" menu could end listing your recent documents, it's supposed to list the document templates you have yourself put into ~/Templates...

---

### Post by howefield on 2011-02-08
> **klein de usa said:**
> where is the file it is reading and how do you disable it?

To disable the list of recent documents open a terminal and type the following command... 

```
rm ~/.recently-used.xbel
```

followed by 

```
touch ~/.recently-used.xbel
```

and finally..
 
```
sudo chattr +i ~/.recently-used.xbel
```

To re-enable logging of recently used documents, use this...
 
```
sudo chattr -i ~/.recently-used.xbel
```

---

### Post by klein de usa on 2011-02-08
hi 
i was confused and didn't understand, i was using the Templates folder for file storage lol but now i know how it works i just didn't realize where the list was coming from, that is a fast way to find something.
                               thank you all

---

