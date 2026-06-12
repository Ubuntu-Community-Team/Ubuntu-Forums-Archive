---
title: "how to shred files"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by imparja2 on 2009-03-29
i want to "kill" this file:

**/usr/lib/firefox/plugins/flashplugin-alternative.so**

I saw on web site that the command should be:

**shred -f -v -z -u file.txt** 

but I don't know where to add the name of the file I want to delete

so what should the complete command be? 

**sudo -shred -f -v -z -u /usr/lib/firefox/plugins/flashplugin-alternative.so**

thanks for the spoon feeding:)

---

### Post by drs305 on 2009-03-29
> **imparja2 said:**
> i want to "kill" this file:
**/usr/lib/firefox/plugins/flashplugin-alternative.so**


Hey, what has that file ever done to you!  ;-)

Well, what you are *looking* for is:
```

sudo shred -vfuz /usr/lib/firefox/plugins/flashplugin-alternative.so

```

What you *need* is another matter. Are you just trying to remove the file? Are you trying to remove all traces of the file from prying eyes? Is this how you delete a file owned by someone else? Not passing judgement, just wonderin'.

Shred seems like a bit of overkill. Removing the file with the "rm" command should be sufficient, but I am not necessarily recommending that either. Read on. 

What you may be experiencing is a fight with permissions. Since you don't own the file, you can't delete it in a normal manner as a normal user. You must gain "admin" powers to remove the file. Usually this is done by temporarily gaining admin rights with "sudo". In this case, you could use "sudo rm ..." to delete the file but *it is dangerous* since if you mess up the command you can irreparably destroy system files (a misplaced space and you could wipe out your entire system). The same is true for using "sudo shred" by the way.

If you use "rm", the file disappears and doesn't go to the trash bin - your's or root's, so unless someone is really interested in recovering the file it shouldn't be a factor. It's not hard for someone with the knowledge to retrieve it, but an everyday user probably wouldn't waste the time accomplishing it. They can get their own *flashplugin-alternative.so* ...

My advice would be to open nautilus or another file browser with root privileges with:
```

gksudo nautilus /usr/lib/firefox/plugins/

```

It will take you to the folder, you will have the permissions to delete the file, and you can be sure you have the correct one. If you accidently delete the wrong file, you can retrieve it from root's trash bin located at /root/.local/share/Trash/files. If you are sure you deleted the correct one, you can empty root's trash or you can bypass the trash by deleting it with SHIFT-DELETE. In that case once you delete it you can't get it back.

Of course, depending on how the file got there in the first place, uninstalling or reversing the process that put the file there is often a better way of doing things. In general, removing things with apt/dpkg/synaptic generally does a better job - if it's an option. It keeps the system more tidy.

Finally, you should read the man page on *shred* ( man shred ).  The man pages can provide good information as well as the proper way to write the command. And occasionally it provides interesting tidbits like why *shred* isn't as effective on some types of ext3 setups.

Perhaps instead of killing it you could give it life without parole.

Best of luck.  :-)

---

### Post by gandaran on 2009-03-29
why do you want to use shred on that file?, there ain't any secrets on that file, a simple rm or rm -r will do.

---

### Post by imparja2 on 2009-03-29
Cheers that was great advice.

I didn't really understand commands like shred remove and kill but now I do.:)

---

