---
title: "possible bug?"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by kubilaycan on 2007-09-16
i use feisty and i realized this:

create a folder "x" > share on network > delete "x" > recreate folder "x" 

then it turns out that "x" is still shared, even though it was deleted.

isnt this a potential security risk?

lets say u create a temporary folder on your desktop to share something and leave it unnamed, i.e. "untitled". then when you are finished u delete it, without disabling the share property. 

then sometime later u create a temporary folder again on your desktop, to extract some sensitive data from an archive, and u leave it unnamed again. and boom it is automatically shared on the network..

so is this a bug?

---

### Post by kidders on 2007-09-17
Hi there,

The behaviour you describe is by design, and in my opinion (for what it's worth!) isn't a bug. I suppose it comes down to what users are most likely to expect the result of something like a deletion to be.

Take symlinks as an example. Imagine you created a temporary file called, say, ~kubilaycan/untitled, and decided to symlink it to ~kidders/untitled for some reason. Deleting the underlying file does not cause the symlink to be deleted (not least because you wouldn't necessarily have the authority to delete it), so any subsequently created replacement ~kubilaycan/untitled would find itself symlinked in ~kidders. Whether I could access it would depend entirely on the umask in place at the time you created the new file.

The last thing most users would expect is for simple file deletions to result in arbitrary system reconfigurations (or further deletions they did not request) ... especially ones that require root privileges! You see, security is not really an issue, given that you always have control over who gets access to your files anyway, regardless of whether they are shared.

I hope that helps a little. Second-guessing its users' intentions would be a risky road for any Linux app to go down, imo.

---

### Post by kubilaycan on 2007-09-17
ok i see 
thx

---

