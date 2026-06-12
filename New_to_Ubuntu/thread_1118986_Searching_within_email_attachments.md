---
title: "Searching within email attachments?"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by ericchan on 2009-04-07
Hello,

I have been using ubuntu for a while, but the one feature from Windows Live Mail that I like is that it automatically searches for text strings within attachments, particularly pdf files.

I tried this in Evolution but it cannot search within pdf files for text, I don't know if this is because it can't view them inline.

Are there any email programs, or even "find" command within terminal, that I can use to search for a particular text string within pdf files that have been downloaded as attachments?

Thanks

---

### Post by ericchan on 2009-04-07
I am reposting here from the general forum, as perhaps my beginner status might get some more suggestions.

In Windows Live mail, a great function was that searching for a name or text string within email also automatically included searching emailed attachments. Thus, a search for a "name" or other text string would pull results for emails that had those terms within a PDF file, even if the subject, sender, or body of the email did not have the string.

Is there any program that does this in linux or ubuntu? I could not find anything on using the "find" command within terminal for this.

Thank you

---

### Post by overdrank on 2009-04-07
Please do not create duplicate threads on the same issue. Threads merged

---

### Post by kaibob on 2009-04-08
> **ericchan said:**
> Are there any email programs, or even "find" command within terminal, that I can use to search for a particular text string within pdf files that have been downloaded as attachments?
Searching PDF files for text strings is an issue that comes up periodically, and I have not seen a good answer. You can open each individual PDF file in Evince or Adobe Reader and search for a text string, but that's not what you want. You could merge the PDF files and then search for a text string in the merged file with Evince or Adobe Reader, but that's about as bad.

I frequently search PDF files for text strings and use the shell script that can be found in the thread referenced below. This shell script would need to be modified to fit your needs and is not something you would want to fool with if you are new to linux. 

Perhaps another forum member can be of more help. 

[http://ubuntuforums.org/showthread.php?t=1084548](http://ubuntuforums.org/showthread.php?t=1084548)

---

