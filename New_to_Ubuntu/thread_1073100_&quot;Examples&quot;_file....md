---
title: "&quot;Examples&quot; file..."
date: 2009-02-18
forum: New to Ubuntu
---

### Post by DonaldJ on 2009-02-18
How do I delete the Examples file..?

---

### Post by mikewu on 2009-02-18
Go into a terminal and type

cd ~ 
rm ./Examples 

That changes you into your home directory and then removes the Examples file.

---

### Post by OutOfReach on 2009-02-18
You can do it by terminal by typing in:
```

sudo rm ~/Examples

```

Type in your password and it should remove the Examples folder.

---

### Post by DonaldJ on 2009-02-18
"sudo rm ~/Examples"
[/CODE]

_____________________________________________________


Thanks Mike and OutofReach


So is the "sudo" is an address-plane in a "registry room"..?
The "rm" is "remove"..?
The "~" "go-to"..?
The "/" is the type of key to a file to seize, or open..?  or a tangent, like a "closet in a hallway"
"Examples" is the target...

Is that correct?

Why is the Examples file locked in root..?

If I were to key "sudo rm ~/Seamonkey" in terminal>enter..  would that remove seamonkey without uninstalling it, but only delete all what is labeled "seamonkey", in that command section..?  and seriously damage the OS..?  Is there a difference between deleting and uninstalling in an Ubuntu OS?..

_________________


If I remove "Examples", is there anything in the OS that is dependent on anything in that file?

I see two logos in the Examples logo-file..  an orange one, and a blue one...  Is that the source of the start up logo..?  or is it just a sample..?

Can I change the start up logo's color with a sudo command?

---

### Post by Nepherte on 2009-02-18
```
rm -r ~/Examples
```
[LIST]
[*]**rm**: the command to remove a file or directory (rm = remove)
[*]**-r**: option of the rm command:recursively remove files. necessary option to remove a directory
[*]**~/Examples**: ~ is a notation for your home directory: /home/yourusername. So ~/Examples is /home/yourusername/Examples.
[*]**sudo**: perform something as root (administrator). Be careful with this. Only use this when you know what you're doing.
[/LIST]

---

