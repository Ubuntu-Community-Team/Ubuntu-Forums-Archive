---
title: "Screenshot upload to illustrate my question?"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by MisFitt on 2010-01-28
I need assistance to install Karmic alongside XP.
The screenshot shows the partition where I store many files,as "boot".When I began to install karmic Karmic wanted to install on this partition.
It's a 500GiB with 2 partitions,around 234G allotted to files I cannot risk losing so i thought it best to seek advice before proceeding.
I had a 160g which I used to use for the operating systems but the first time I put Karmic in it warned of "imminent failure" of that HD so it's now unplugged and I haven't replaced it.
Thanks

---

### Post by howefield on 2010-01-28
Your screenshot uploaded fine, what's the question ?

---

### Post by audiomick on 2010-01-28
Hi
I think you did want you wanted already, there is a screenshot of gparted attached.

For the record:
below the window for typing text, click on "manage attachments" in the "attach files" box.
in the pop up, click on "search" to the right of one of the fields in "upload file from your computer"
click on "upload file" in the lower right of that section.

That's it. You can ignore the URL thing. That is for getting a file from a URL, I suppose. I've never used it.

Say hallo to Melbourne for me... :)

---

### Post by MisFitt on 2010-01-28
Yes,sorry about that.

---

### Post by MisFitt on 2010-01-28
she says "Hi" back and wants to know if this is home?

---

### Post by audiomick on 2010-01-28
> **MisFitt said:**
> she says "Hi" back and wants to know if this is home?

I went to Uni at La Trobe and live in Melbourne for a total of about 13 years before  I came here, so yes, in a way it is home.;)
Now that I have seen some of the rest of the world, I know what a truly great city Melbourne is.

What is the problem you wanted to illustrate?

---

### Post by theozzlives on 2010-01-28
Why is your XP partition a logical one?

---

### Post by audiomick on 2010-01-28
> **theozzlives said:**
> Why is your XP partition a logical one?

Don't think it is. Have another look. Sda2, which must be a primary with that number, is an NTFS and labelled as boot.
edit: except there is nothing in sda2:confused:

 The extended is probably a data partition.

I still want to know what the original problem was...

---

### Post by MisFitt on 2010-01-28
I wanted to install karmic as a dual boot alongside XP but during the install process Karmic wanted to install on the partition where I know many files I need to keep are,/dev/sda2.
I currently don't have enough space on my external HD to back them up so I need to be very,very careful.(sda2 has about 160-70G's worth of files on it)

---

### Post by audiomick on 2010-01-28
Is sda2 also where the xp install is? I think it must be, because as far as I know, windows wont boot from an extended partition.

What is in the extended partition, sda5?

---

### Post by MisFitt on 2010-01-28
sda5 is where XP is and where I would like to install Karmic to.
/dev/sda2 holds all my files

---

### Post by sandyd on 2010-01-28
bugs are useful.
is this what your getting?
[https://bugs.launchpad.net/ubuntu/karmic/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/karmic/+source/libatasmart/+bug/438136)
if it is, let it be... ill be fixed soon enough..... if ever.

---

### Post by audiomick on 2010-01-28
OK, if you are really sure about what is where, choose the manual partitioning option in the installer and tell it to install there. You will have to shrink the partition first, and create a partition for Ubuntu and a swap. You might also consider creating a partition for /home as well. That allows you to simply re-mount the /home in the event of a future re-install.

---

### Post by audiomick on 2010-01-28
I am still uneasy about this. I was sure that a windows install has to be in a primary partition to work.

Can you go here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
follow the instructions, and post the result here? You will need to boot from the live CD to do it.
When you post the result, use the # button to put code tags around it. It is pretty long.

---

### Post by MisFitt on 2010-01-28
carlee-I really don't understand the question,I haven't even installed Karmic yet

---

### Post by sandyd on 2010-01-28
> **MisFitt said:**
> <snip>[B]
but the first time I put Karmic in it warned of "imminent failure" of that HD so it's now unplugged and I haven't replaced it.
Thanks[/B]
^^
this

---

### Post by Miljet on 2010-01-28
> I am still uneasy about this. I was sure that a windows install has to be in a primary partition to work.

+ 1
I really think the OP has the partitions confused.

---

### Post by MisFitt on 2010-01-28
Michael,before I do this-what are "code tags"?
You're asking me to copy/paste the results,easy enough..?

---

### Post by audiomick on 2010-01-28
> **MisFitt said:**
> Michael,before I do this-what are "code tags"?
You're asking me to copy/paste the results,easy enough..?

In the window for writing posts amongst the business up the top there is a #

If you click on that, it inserts tags that look a bit like this
[like this][/like this] but they have "code" in them.
Either type or paste between them, or select the text and then push the button.

It puts the text
```
in a box like this
```
and adds a scroll bar if it is a long text.

The button that looks like a speech balloon is for quotes.

Yes, just copy and paste the results file here. The process generates a .txt file on the desktop. If you click on it, it will open in an editor, and you can copy it from there.

---

### Post by MisFitt on 2010-01-28
I'm trying it but it keeps saying 'no such file or directory"

---

### Post by audiomick on 2010-01-28
where are you up to?

---

### Post by MisFitt on 2010-01-28
Pasting the command
sudo bash ~/Downloads/boot_info_script*.sh 
into the terminal

---

### Post by audiomick on 2010-01-28
So you are running from a live CD, right?
And you have downloaded the script.

Go to places> the first entry, I think it is "ubuntu" in the live environment. There should be a folder in there called "Downloads", and in there should be the file "boot_info_script*.sh"

Can you find it?

---

### Post by MisFitt on 2010-01-28
thanks Carlee,I'll check that out.Why do you think it could be a bug?
It is a fairly old 160G ide HD so I assumed it could very well be "tired"
so there is hope for this.I do hope so,I loved having it purely for OS's,THANKS

---

### Post by MisFitt on 2010-01-28
The first place is the "home folder" and there's nothing in any  folders and I've gone down the list,nothing.In "computer" however it does show the hard drive and partitions and windows is in the slightly smaller one as I said,my files in the other which strangely is labelled "boot" in gparted,the screenshot.
The size varies,eg-in windows xp is in the partition D:,232G which in gparted is /dev/sda2, 231.65G.
In windows C: has my files,234G which in gparted is /dev/sda5,231.62G.
The labels I know are the wrong way around but that is how it is.

---

### Post by dolphinaura on 2010-01-28
> **MisFitt said:**
> thanks Carlee,I'll check that out.Why do you think it could be a bug?
It is a fairly old 160G ide HD so I assumed it could very well be "tired"
cause theirs a lot of people having false positives. we cannot tell which ones are false and which ones are actually failures just by looking at the notifications
you **will** have to double check the drive yourself to make sure that its not the bug thats leading you astray

---

### Post by audiomick on 2010-01-28
Ok, I guess you are on the right track. Try the manual partitioning in the install.
I'll look in tomorrow.
Good luck.

---

### Post by MisFitt on 2010-01-28
Thanks heaps Michael,appreciate your help,have a good one!

---

### Post by MisFitt on 2010-01-29
Hey thanks Dolphinaura,so I see.
Can you recommend the "best" way to test it?
It'd be terrific if I could use it again,was a great size to have.

---

### Post by audiomick on 2010-01-29
> **MisFitt said:**
> Hey thanks Dolphinaura,so I see.
Can you recommend the "best" way to test it?
It'd be terrific if I could use it again,was a great size to have.

Don't know if this is "best", but it should test what you need, I think.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
Looks a bit daunting, but it isn't that hard, actually. I am pretty sure it will work from the live CD.
Basically, you have to install the thing, run the test, then go and look what you got. It doesn't automatically pop up results.

---

### Post by MisFitt on 2010-01-29
Thanks again,will give it a try.
BTW,I have my dual boot successfully installed,where I want it,no probs.
Thanks very much for your advice,take care

---

### Post by audiomick on 2010-01-29
Great to hear it.
Look after yourself.

---

