---
title: "Lost 150Gigs of drive space"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by Tighearna on 2009-03-15
I seem to have lost over 150 Gigs of drive space, and I can't find it. LOL

I noticed that I was running out of drive space and couldn't figure out why. Then I remembered that I had installed Simple Backup Suite 0.10.4.

Since you have to be root to access the backup folder (/var/backup/), I opened a terminal and ran sudo nautilus. I saw that the /var/backup/ was 150 Gigs. Then I thought, "I don't really need all that backup on a home system." So I opened Simple backup, changed the backup location to /home/backup/ and set it for 7 days thinking that I could burn it to a DVD-RW and that way I would still have a backup if needed and not use all that space.

Then I moved /var/backup/ to the trash, however, it didn't appear in the trash. I thought that is odd. I emptied that trash. Now I am still missing the drive space and I have no idea how to find it and how to recover the space.

Any ideas?

P.S. Since this is a home system, and if something happened I could use the live cd to access the file system is a backup really even needed?

Thank you,
Jim

Almost forgot I'm using ubuntu intrepid

---

### Post by hyper_ch on 2009-03-15
how did you move it to trash? and what trash did you empty?

---

### Post by Tighearna on 2009-03-15
While in sudo nautilus I highlighted the folder, right clicked and selected move to trash. I didn't see anything in either the sudo nautilustrash icon on the left of the window or on the desktop. So I emptied both of them.

---

### Post by hyper_ch on 2009-03-15
it's in root trash

---

### Post by Tighearna on 2009-03-15
I go to root trash, (terminal, sudo nautilus, trash). I doesn't have the symbol for anything being in the trash folder.
I right click on it and it doesn't give me the option to empty trash.
Left click on the trash icon (root trash still) and I get an error message saying that "The folder contents could not be displayed. Sorry, could not display all the contents of "trash" : Operation not supported"

Now that I'm typing this 150 Gigs is a HUGE file, Should I just go have a cup of coffee and give it a chance to load? Then select empty trash? Is there an easier/faster way to do this? Terminal commands of anything?

---

### Post by hyper_ch on 2009-03-15
check via terminal if root trash is empty... I think it's not.

---

### Post by Tighearna on 2009-03-15
That was it. Perfect.

Thank you.

Any thoughts on the other issue. Is keeping the back basically unneccesaary anyway?

---

### Post by hyper_ch on 2009-03-15
for future reference, if you shift-delete things they won't got into trash but directly be deleted.

Same goes if you use the "rm" command from the cli.

---

### Post by billgoldberg on 2009-03-15
I'll start by saying you'll need to use "gksudo nautilus" instead of "sudo nautilus".

Sudo is meant for command line work only.

It will most likely work on GUI apps most of the time, but things could get messed up.


--

If you are serious about back ups, buy an external hard drive and back up to that.

I don't see the point in backing up to your local hard drive. 

There are also online solutions.

Check out spideroak.com, they have an Ubuntu client and offer 2gb space for free.

---

### Post by Tighearna on 2009-03-15
> for future reference, if you shift-delete things they won't got into trash but directly be deleted.

Same goes if you use the "rm" command from the cli. 

I wasn't aware of that. Thank you :)

> I'll start by saying you'll need to use "gksudo nautilus" instead of "sudo nautilus".

Will do, Thank you.

As far as the backup. All of the critical docs are public key encypted and uploaded to our server. I was concerned with mail, settings etc. but now that I think about it. That all can fit on a thumb drive.

I'm still trying to get my mind to think Nix instead of Windows.

Thank you both for the help and input.

---

### Post by theozzlives on 2009-03-15
Look for /var/backup/.Trash

---

