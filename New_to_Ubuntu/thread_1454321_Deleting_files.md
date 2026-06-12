---
title: "Deleting files"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by newport_j on 2010-04-14
I have a file that I open up in append mode. I want to write new things to it and append them to this file during the execution of the program. 

I also do not want to write things to it during subsequent executions of the program. So what command in C can I give that will essentially remove the program. This is given only once during an execution of the program. 

I know the various fopen modes, but which one is this, just to remove the old file.

Newport_j

---

### Post by falconindy on 2010-04-14
I'm not exactly clear on what you're trying to accomplish, but if you're looking to delete a file, use unlink(3). You'll need to provide an absolute path to the file -- if you only have a relative path, you can use realpath(3).

---

### Post by quadproc on 2010-04-14
> **newport_j said:**
> I have a file that I open up in append mode. I want to write new things to it and append them to this file during the execution of the program. 

I also do not want to write things to it during subsequent executions of the program. So what command in C can I give that will essentially remove the program. This is given only once during an execution of the program. 
I am not sure that I understand what you need to do; it sounds like you want to create this file during the first execution of the program and then leave the file alone in the future, even if the same program is executed again.  if so, your program can try to open the file to read it; if that fails because the file doesn't exist then you can open it for write in the append mode.  If that succeeds then your program should close the file and not execute any code that would try to write to it.  If the file was opened for writing then when the program finishes with the file, the program can close it and then change its permissions to read only.  You also should consider what would happen if your program doesn't close the file, perhaps because the program is killed by a user, by a power failure, by somebody pushing the reset button,by running out of disk space, etc.  You will need to plan ahead for these contingencies.

quadproc

---

### Post by newport_j on 2010-04-15
I have a program that I run that appends output to a file during a run. I run it and it creates a very large file. The file is opened in the append mode. When I run the program again, I get the new output appended to the old output in the same file. This I do not want. If I remember to delete the file, then it only has the most recent output from the run of the data. This I do want.

Now, I would like to automate that delete/empty file  every time I run the program. Thus I do not have to remember to delete this file before running the program. There have been too many times where I forget to delete the file between runs and old output is now at the top of the most recent output file with the new output succeeding it. I, again, do not want this.  

So what c statement can I include in my program before I open the output file for appending that will simply empty the output file of its current/old contents.

Newport_j

---

### Post by r-senior on 2010-04-15
Wouldn't it make more sense, rather than opening a file in the program, to send the output via stdout? Just using standard printf, etc. You can then redirect the output using the shell which will overwrite the old file if you redirect using ">".

$ myprog > output.txt

This also increases flexibility - you could pipe the output through gzip to compress the output file for example:

$ myprog | gzip > output.txt.gz

Alternatively, check if the output exists and abort with an error?

---

### Post by quadproc on 2010-04-15
> **newport_j said:**
> I have a program that I run that appends output to a file during a run. I run it and it creates a very large file. The file is opened in the append mode. When I run the program again, I get the new output appended to the old output in the same file. This I do not want. If I remember to delete the file, then it only has the most recent output from the run of the data. This I do want.

OK, understood.  Just open your file for writing - that is "w" rather than "a".  If the named file does not already exist then the system will create it (and it will be empty until you write to it).  If the named file does already exist then its contents will be discarded and its length set to 0.  Subsequent writes will put data into it.

Opening a file in append mode is what the shell does when you use >> redirection.  Opening a file in write mode is what the shell does when you use > redirection.

I hope that this solves your problem.  If so, then please mark the thread as "solved".  Otherwise, ask us for more information.  Thanks.

quadproc

---

### Post by newport_j on 2010-04-16
I think opening the file for writing will certainly delete or empty the file at the initial stages of a program run. But, as the program progesses it will continue to do this. I want all data generated in a run appended to this file. I not want just the last part when the file is written to for the last time during program run. 
 
If I could open a file for writing and then immedialletley after change it to append mode that would be ideal. Can this be done?
 
Newport_j

---

### Post by avidday on 2010-04-16
> **newport_j said:**
> I think opening the file for writing will certainly delete or empty the file at the initial stages of a program run. But, as the program progesses it will continue to do this. 

No, that isn't how it works. If you only open the file once per application run, it only gets truncated once.

---

### Post by quadproc on 2010-04-16
> **newport_j said:**
> I think opening the file for writing will certainly delete or empty the file at the initial stages of a program run. But, as the program progesses it will continue to do this.No, as avidday mentioned, the truncation occurs once, when the file is opened.  If you do not close the file between writes then the new data will continue to be appended to the file.  Of course, once you have all of the data then you need to close the file before your program exits so just do a single fclose when the program is wrapping up.

A file in Unix or Linux is a stream of bytes.  Unless you explicitly do something to reposition the file's internal data pointer then the next byte goes onto the end of the stream of bytes.

Incidentally, if you use a different process to examine the contents of a file while it is being written (for example, you could use a terminal and enter "cat <the_file>"), you will most likely not see a good representation of what the file will eventually look like.  The reason for this is that the data is buffered before being transferred to the disk; if the buffer has not filled up yet then that portion of the data has not yet reached the disk.  When the file is closed then the last of the buffered data will be flushed onto the disk and it will thereafter look like it should.

quadproc

---

### Post by newport_j on 2010-04-20
Okay, in a situation where the write mode is "w", then one must open it once at the start of the program and close it at the end. That sounds like the best idea.

However to do that, the fopen and fclose statements cannot be put in the function that is writing the output by being repeatedly called or that would be result in output being written to a file from only the last time that the function was called.

The ideal method is to open the file in the main program/function at the top where it begins and close at the bottom of the program when it ends.

This would require that statement such as:

FILE *fid1, fid2;

to be in the main program/function. They then must be global variables since the actual writing of the file will be in the function that was previously mentioned.

So you fopen the file at the start of the program and fclose it at the end. The actual writing is done in a separate repeatedly called function. This seems to work.

Is this the correct way to do this?

Newport_j

---

### Post by talonmies on 2010-04-20
> **newport_j said:**
>  

This would require that statement such as:

FILE *fid1, fid2;

to be in the main program/function. They then must be global variables since the actual writing of the file will be in the function that was previously mentioned.

They most certainly don't have to be global scope. You can, and probably should pass the FILE handle by pointer or reference to the subroutines that need access to a give file, for either read or write. Do so also opens up a number of other very useful possibilities, like passing stdin and stdout instead of a an open file, which is useful for debugging and piping program input and output.

---

