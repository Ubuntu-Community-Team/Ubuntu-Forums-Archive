---
title: "bash script to iterate directory"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by noorez on 2010-11-08
Hi,

I would like to start installing sun java manually as the repositories don't really stay up to date. I need to setup the alternatives my self then. Here is what I need to do:

```

update-alternatives --install /usr/bin/java java /opt/java/<current_java>/bin/java --slave [all other binaries except 'java']

```

Can someone help with this?

I would like a bash script to automate this for me.

---

### Post by Crusty Old Fart on 2010-11-09
Are you hoping for something like this:
```

#!/bin/bash
update-alternatives --install /usr/bin/java java /opt/java/<current_java>/bin/java --slave [all other binaries except 'java']

```Take that code, copy it to a file, name the file: whatever.sh

Make the file: whatever.sh executable:
```

chmod 700 whatever.sh

```I'm a bit confused by your question, mostly because my answer to it seems so simple and obvious. I'm assuming that your "update-alternatives..." command is correct, and all you wanted to do was wrap it up in a bash script. If that's all you needed, then my answer should work. If not, please reply with something to give me an idea of what I'm missing.

Your title indicates that you want to iterate a directory. Are you referring to the directory in your command that is indicated by: <current_java>?
As in: every time you run the bash script, that directory gets iterated...say maybe by appending its name with the current date, or a number?

You can see, I'm lost.

---

### Post by noorez on 2010-11-09
hey,

for the  " [all other binaries except 'java']  ", what I would like is a way to concatenate to the command:

```

update-alternatives --install /usr/bin/java java /opt/java/<current_java>/bin/java

```

```

--slave "/usr/bin/javac" "javac" "/opt/java/<current_java>/bin/javac" --slave ...

```

the list of files in /opt/java/<current_java>/bin is quite long so I need a script to construct the command for me. the --slave should not contain "java" as this is the master link.

---

### Post by Crusty Old Fart on 2010-11-09
Ok, noorez:

I think I have a better understanding of what you want to do now. Funny that your last post hit the forum just as I submitted an edit to mine.

Just so you know a bit about my skill levels: I'm good at shell scripts, but this problem is my first exposure to the "update-alternatives" command.

After I jam my nose into the man page for "update-alternatives", I'll have a much better idea of what we're dealing with.

Your last post helped a lot. Thanks for clearing things up for me. I'll let you know as soon as I have something thrown together that we can modify to work the way you want it to.

It shouldn't take too long, hopefully, I'll have something by tomorrow morning.

---

### Post by Crusty Old Fart on 2010-11-09
I need a check on my understanding of the concept here.

We want to end up with a script that builds a huge command that might be represented by concatenating all of the following:
```

update-alternatives --install /usr/bin/java java /opt/java/<current_java>/bin/java
--slave "/usr/bin/javaC" "javaC" "/opt/java/<current_java>/bin/javaC"
--slave "/usr/bin/javaD" "javaD" "/opt/java/<current_java>/bin/javaD"
--slave "/usr/bin/javaE" "javaE" "/opt/java/<current_java>/bin/javaE"
--slave "/usr/bin/javaF" "javaF" "/opt/java/<current_java>/bin/javaF"
--slave "/usr/bin/javaG" "javaG" "/opt/java/<current_java>/bin/javaG"
--slave "/usr/bin/javaH" "javaH" "/opt/java/<current_java>/bin/javaH"

***[COLOR=Blue]...and so on until we have installed every file available from the update...[/COLOR]***

```So...we need a list of every file on your system in **/opt/java/<current_java>/bin** which we can parse for every file name to be substituted for the names represented above by "javaC" through "javaH"...excepting, of course, the masterlink name: "java"

Right? Am I getting this?

---

### Post by noorez on 2010-11-10
Yes. That seems to be correct.

---

### Post by Crusty Old Fart on 2010-11-10
Alrighty noorez:

I'm uploading a script that we can test. You'll need to make it executable to run it. In its present form, all it will do is dump output to your screen. It won't actually perform the update-alternatives command, but after dumping loop counter values and file names, it will show you the completely concatenated command. When you examine the loop counter numbers, you should see that at some point, a number is skipped over. That occurs when the masterlink: "java" file is excluded. You should not find a file named "java" in the output of the filenames from the loop. Check this carefully. At the very end of the output you should see a variable named: UPDTCMD. This variable contains the entire concatenated command that I think you're looking for. This should be checked carefully as well.

When we have corrected any errors that I may have made. I'll give you a version of the script that will actually perform the update. Please don't muck around with the source code. It will be a lot easier for me to fix any problems if I can be confident that you're only running versions of the scripts that I provide. Thanks in advance for your cooperation.

Here's the source of what's in the attached file: noorez_testv1.sh
```

#!/bin/bash 

echo -e "\n\n*********************************************"
echo "*   This script is running in test mode.    *"
echo "* No changes are being made to your system. *"
echo -e "*********************************************\n\n"

# =====================
# Initialize variables.
# =====================
UPDTCMD="update-alternatives --install /usr/bin/java java /opt/java/<current_java>/bin/java " 

# ==================================================================================================
# Determine the number of files in the target directory excluding subdirectories and their contents.
# ==================================================================================================
FILETOT=$(find "/opt/java/<current_java>/bin" -maxdepth 1 -type f | wc -l)
echo "FILETOT =" $FILETOT

# ==============
# Build command.
# ==============
i=1
while [ $i -le $FILETOT ] 
do
  FNAME=$(find "/opt/java/<current_java>/bin" -maxdepth 1 -type f | sed 's/\/opt\/java\/<current_java>\/bin\///g' | awk -v k=$i 'FNR == k {print}')

  # ==============================================
  # Trap and exclude the masterlink filename: java
  # ==============================================
  while [ $FNAME == java ]
  do
    i=$[$i + 1]
    FNAME=$(find "/opt/java/<current_java>/bin" -maxdepth 1 -type f | sed 's/\/opt\/java\/<current_java>\/bin\///g' | awk -v k=$i 'FNR == k {print}')
  done 

  echo "i =" $i 
  echo "FNAME =" $FNAME

  # =================================
  # Successively concatenate command.
  # =================================
  CATCMD=$(echo -e " --slave \"/usr/bin/"$FNAME"\"" "\"$FNAME\"" "\"/opt/java/<current_java>/bin/"$FNAME"\"") 
  UPDTCMD=$(echo $UPDTCMD $CATCMD)
  i=$[$i + 1]
done

# ======================================
# Dump command building result to shell.
# ======================================
echo "UPDTCMD =" $UPDTCMD

echo -e "\n\n*****************"
echo "* All finished. *"
echo -e "*****************\n\n"
exit 0


```I have to comment on the mondo size of the command that's generated by this. Are you sure that works? I know the man page seems to indicate that it can accept an unlimited number of --slave options. But for crying out loud, it seems REALLY nutzoid to me.

---

### Post by noorez on 2010-11-11
It seems to work. I'm just testing it out right now.

---

### Post by Crusty Old Fart on 2010-11-11
If you'd like to test the command that it generates, you can drag your mouse over the text that occurs after: UPDTCMD = 

Right click and copy it.

Then paste it to your shell after the command prompt and hit Enter. ([COLOR=Red]**<--_Edit_**[/COLOR]: I think you may need to insert: **sudo** between the prompt and the beginning of the update command)

---

### Post by noorez on 2010-11-11
Hey,

I had to make a minor adjustment to the script. It was a mistake on my part but I do apologize for not catching it earlier:
```

update-alternatives --install /usr/bin/java java /opt/java/<current_java>/bin/java priority

```
I just forgot to add on a priority to the alternatives command.

As for giving it a test, I had to run it in a fedora machine as I have not been able to access my Ubuntu box for a bit, however it does work! (with some minor changes to the directories though).

I would like to test something new though. As you mentioned, the command generated is quite large. So instead lets try this

```

update-alternatives --install /usr/bin/java java /opt/java/<current_java>/bin/java priority --slave *

```

where this command is run for each item in the java/bin folder excpet for 'java'.

---

### Post by Crusty Old Fart on 2010-11-11
Got it...I'll make the change to add on a priority to the alternatives command.

Yup...as I was writing the code, I thought about the same thing: just doing one --slave... option at a time.

I'll put up a new test version as soon as I make the changes.

After we iron out the details to get it running as you want it, I may be adding some options to it that you can enable or disable in a top section, similar to how the options in /etc/default/grub can be modified if you are comfortable making modifications in that way. So, are you comfortable setting options in that manner?

---

### Post by noorez on 2010-11-11
It would be fine to make the changes.

Here are some options to consider:

1) the location of the java installation, for example:  /usr/java/jdk1.6.0_22/
2) the priority for the alternative system, for example 200000

Another quick note. I'm trying to understand your script, but I'm still new to bash scripting. How can I interpret the following:

```

find "/opt/java/<current_java>/bin" -maxdepth 1 -type f | sed 's/\/opt\/java\/<current_java>\/bin\///g' | awk -v k=$i 'FNR == k {print}')

```

---

### Post by Crusty Old Fart on 2010-11-11
Okay...here we go...I've uploaded:**[COLOR=Blue] noorez_testv2.sh[/COLOR]** and dumped the source into the code box below:
```

#!/bin/bash 

echo -e "\n\n*********************************************"
echo "*   This script is running in test mode.    *"
echo "* No changes are being made to your system. *"
echo -e "*********************************************\n\n"

# =====================
# Initialize variables.
# =====================
INITCMD="update-alternatives --install /usr/bin/java java /opt/java/<current_java>/bin/java priority " 

# ==================================================================================================
# Determine the number of files in the target directory excluding subdirectories and their contents.
# ==================================================================================================
FILETOT=$(find "/opt/java/<current_java>/bin" -maxdepth 1 -type f | wc -l)

# ==================
# Construct command.
# ==================
i=1
while [ $i -le $FILETOT ] 
do
  FNAME=$(find "/opt/java/<current_java>/bin" -maxdepth 1 -type f | sed 's/\/opt\/java\/<current_java>\/bin\///g' | awk -v k=$i 'FNR == k {print}')

  # ==============================================
  # Trap and exclude the masterlink filename: java
  # ==============================================
  while [ $FNAME == java ]
  do
    i=$[$i + 1]
    FNAME=$(find "/opt/java/<current_java>/bin" -maxdepth 1 -type f | sed 's/\/opt\/java\/<current_java>\/bin\///g' | awk -v k=$i 'FNR == k {print}')
  done 

  # ====================
  # Concatenate command.
  # ====================
  CATCMD=$(echo -e " --slave \"/usr/bin/"$FNAME"\"" "\"$FNAME\"" "\"/opt/java/<current_java>/bin/"$FNAME"\"") 
  UPDTCMD=$(echo $INITCMD $CATCMD)
  i=$[$i + 1]

  # ==========================================
  # Dump command construction result to shell.
  # ==========================================
  echo $UPDTCMD
done

echo -e "\n\n*****************"
echo "* All finished. *"
echo -e "*****************\n\n"
exit 0

```Thanks for letting me know that you're comfortable modifying an options section in the script and suggesting some options to include in it. I'll get to that in version 3 later.

With regard your question:
> 
How can I interpret the following:
```

find "/opt/java/<current_java>/bin" -maxdepth 1 -type f | sed 's/\/opt\/java\/<current_java>\/bin\///g' | awk -v k=$i 'FNR == k {print}')

```That line of code does not lend itself to a quick answer to someone without a fair amount of experience writing shell scripts. So, it will take me some time to put together an answer that will help you understand how it works. I'm kind of short on time today, but I'll try to have something written up for you before tomorrow night. It's a good question and deserves an answer that will leave you educated rather than confused. I'm hoping to come up with a way to explain it that will do that. If I'm successful, you'll have learned more about scripting and I will have become a better teacher.

Lastly, the output from the attached script is a lot different. It will look like it's writing actual commands into your shell. Don't freak out about that. They don't get executed. The clue to that is: there won't be a command prompt in front of any of them.

Thanks for your replies. I'm enjoying working with you on this little project.

---

### Post by Crusty Old Fart on 2010-11-12
Version 3 -- With configuration section.

Source in attached file: **[COLOR=Blue]noorez_testv3.sh[/COLOR]**[COLOR=Blue][COLOR=Black]
```

#!/bin/bash 
  set -e  #<--Abort script immediately on error.
# set -x  #<--Turn debug tracer on.

#######################################################
#      TOP OF PARAMETER CONFIGURATION SECTION         #
#######################################################

# =====================================================
# MASTER LINK CONFIGURATION:
# =====================================================

# -----------------------------------------------------
# Generic name for the master link:
#   Syntax example:
#     MSTR_LINK="/foo/bar/goo/javalink" 
# -----------------------------------------------------
      MSTR_LINK="/usr/java/jdk1.6.0_22/java" 

# -----------------------------------------------------
# Symlink name in the alternatives directory:
#   Syntax example:
#     MSTR_NAME="javalink" 
# -----------------------------------------------------
      MSTR_NAME="java"

# -----------------------------------------------------
# The alternative being introduced for the master link:
#   Syntax example:
#     MSTR_PATH="/boo/far/noob/dar/javalink"
# -----------------------------------------------------
      MSTR_PATH="/opt/java/<current_java>/bin/java"

# -----------------------------------------------------
# Priority:
#   Syntax example:
#     PRIORITY=1419
# -----------------------------------------------------
      PRIORITY=200000

# =====================================================
# SLAVE CONFIGURATION:
# =====================================================

# -----------------------------------------------------
# Generic name for the slave link directory:
#   Syntax example:
#     SLV_LINK_DIR="/foo/bar/goo/"
# -----------------------------------------------------
      SLV_LINK_DIR="/usr/java/jdk1.6.0_22/"

# -----------------------------------------------------
# Symlink name in the alternatives directory:
# -----------------------------------------------------
#  ~~~ THIS PARAMETER IS GENERATED BY THE SCRIPT ~~~ 

# -----------------------------------------------------
# The alternative path for the slave link directory:
#   Syntax example:
#     SLV_PATH_DIR="/boo/far/noob/dar/"
# -----------------------------------------------------
      SLV_PATH_DIR="/opt/java/<current_java>/bin/"

#######################################################
#      BOTTOM OF PARAMETER CONFIGURATION SECTION      #
#######################################################

echo -e "\n\n*********************************************"
echo "*   This script is running in test mode.    *"
echo "* No changes are being made to your system. *"
echo -e "*********************************************\n\n"

# =====================
# Initialize variables.
# =====================
INITCMD="update-alternatives --install $MSTR_LINK $MSTR_NAME $MSTR_PATH $PRIORITY " 

# ==================================================================================================
# Determine the number of files in the target directory excluding subdirectories and their contents.
# ==================================================================================================
FILETOT=$(find "$SLV_PATH_DIR" -maxdepth 1 -type f | wc -l)

# ==================
# Construct command.
# ==================
i=1
while [ $i -le $FILETOT ]; do 
  FNAME=$(find "$SLV_PATH_DIR" -maxdepth 1 -type f | \
          sed "s/$(echo $SLV_PATH_DIR | sed 's/\//\\\//g')//g" | \
          awk -v k=$i 'FNR == k {print}')

  # ==============================================
  # Trap and exclude the masterlink filename: java
  # ==============================================
  while [ $FNAME == java ]; do
    i=$[$i + 1]
    FNAME=$(find "$SLV_PATH_DIR" -maxdepth 1 -type f | \
            sed "s/$(echo $SLV_PATH_DIR | sed 's/\//\\\//g')//g" | \
            awk -v k=$i 'FNR == k {print}')
  done 

  # ====================
  # Concatenate command.
  # ====================
  CATCMD=$(echo -e " --slave \"$SLV_LINK_DIR"$FNAME"\"" "\"$FNAME\"" "\"$SLV_PATH_DIR"$FNAME"\"") 
  UPDTCMD=$(echo $INITCMD $CATCMD)
  i=$[$i + 1]

  # ==========================================
  # Dump command construction result to shell.
  # ==========================================
  echo $UPDTCMD
done

echo -e "\n\n*****************"
echo "* All finished. *"
echo -e "*****************\n\n"
exit 0


```[/COLOR][/COLOR]

---

### Post by Crusty Old Fart on 2010-11-12
How can I interpret the following:
> 
```

find "/opt/java/<current_java>/bin" -maxdepth 1 -type f | sed 's/\/opt\/java\/<current_java>\/bin\///g' | awk -v k=$i 'FNR == k {print}')

```This line of code takes the standard output (stdout) from the [COLOR=Blue]**find**[/COLOR] command, pipes (**[COLOR=Red]|[/COLOR]**) it into the standard input (stdin) for the [COLOR=Blue]**sed**[/COLOR] command, and finally takes the stdout from the [COLOR=Blue]**sed**[/COLOR] command and pipes (**[COLOR=Red]|[/COLOR]**)  it into the stdin for the [COLOR=Blue]**awk**[/COLOR] command. The resultant output is the stdout from the [COLOR=Blue]**awk**[/COLOR] command, which is a single file name.


In the following line, the pipes (**[COLOR=Red]|[/COLOR]**) are shown in red and the **[COLOR=Blue]command names[/COLOR]** in blue.[INDENT][SIZE=2][SIZE=2][COLOR=Blue]**find**[/COLOR][/SIZE][SIZE=2] "/opt/java/<current_java>/bin" -maxdepth 1 -type f **[COLOR=Red]|[/COLOR]** [/SIZE][SIZE=2][COLOR=Blue]**sed**[/COLOR][/SIZE][SIZE=2]  's/\/opt\/java\/<current_java>\/bin\///g' **[COLOR=Red]|[/COLOR]** [/SIZE][SIZE=2][COLOR=Blue]**awk**[/COLOR][/SIZE][SIZE=2] -v k=$i 'FNR == k  {print}')

[/SIZE] [/SIZE][/INDENT]Let's take this line apart so we can discover the data that is passing through the pipes, and finally coming to us as output, by examining each of the three commands separately:[INDENT][SIZE=2][COLOR=Blue]**find**[/COLOR] "/opt/java/<current_java>/bin" -maxdepth 1 -type f [B][COLOR=Red]
|
[/COLOR][/B][COLOR=Blue]**sed**[/COLOR]  's/\/opt\/java\/<current_java>\/bin\///g'
[B][COLOR=Red]|
[/COLOR][/B][COLOR=Blue]**awk**[/COLOR] -v k=$i 'FNR == k  {print}')[/SIZE]

[/INDENT]
[LIST]
[*]The **[COLOR=Blue]find[/COLOR]** command: searches for files in a directory hierarchy. In our case, we're using three options in our **[COLOR=Blue]find[/COLOR]** command: **"/opt/java/<current_java>/bin"**, [COLOR=Red]**-maxdepth 1**[/COLOR], and [COLOR=Green]**-type f**[/COLOR] as follows:[INDENT][SIZE=2]**[COLOR=Blue]find[/COLOR] ****"/opt/java/<current_java>/bin" [COLOR=Red]-maxdepth 1[/COLOR][COLOR=Green] -type f [/COLOR]**[/SIZE][/INDENT]
[/LIST]
[INDENT][INDENT]Let's see what we get for output from this command as we run it with the first option and then add the other two, one at a time. The first option will tell the **[COLOR=Blue]find[/COLOR]** command to only look for the contents of the directory: **/opt/java/<current_java>/bin**
```

**[COLOR=Blue]find[/COLOR] ****"/opt/java/<current_java>/bin"**

***~~~ output ~~~***

/opt/java/<current_java>/**[COLOR=Red]bin[/COLOR]**
/opt/java/<current_java>/bin/java0
/opt/java/<current_java>/bin/java1
/opt/java/<current_java>/bin/java2
/opt/java/<current_java>/bin/java3
/opt/java/<current_java>/bin/java
/opt/java/<current_java>/bin/**[COLOR=Red]JAVAMA[/COLOR]**
/opt/java/<current_java>/bin/**[COLOR=Red]JAVAMA[/COLOR]**/**[COLOR=Blue]javamobay[/COLOR]**
/opt/java/<current_java>/bin/**[COLOR=Red]JAVAMA[/COLOR]**/**[COLOR=Blue]bop_beebop_bay[/COLOR]**

```It gave us a list that included the target directory (**[COLOR=Red]bin[/COLOR]**), all of the files within the target directory, its subdirectory (**[COLOR=Red]JAVAMA[/COLOR]**) and the files within the subdirectory (**[COLOR=Red]JAVAMA[/COLOR]**/**[COLOR=Blue]javamobay[/COLOR]** and **[COLOR=Red]JAVAMA[/COLOR]**/**[COLOR=Blue]bop_beebop_bay[/COLOR]**). For our script, we don't want to have files that exist within subdirectories included in the output. We can exclude them by restricting the depth to which **[COLOR=Blue]find[/COLOR]** descends into the directory hierarchy. We don't want it to go any deeper than our target directory (**/opt/java/<current_java>/bin**), the contents of which, are at a depth of 1. This is accomplished by adding our second option ([COLOR=Red]**-maxdepth 1**[/COLOR]) to our **[COLOR=Blue]find[/COLOR]** command. So, let's see what we get for output when we do that.
```

**[COLOR=Blue]find[/COLOR] ****"/opt/java/<current_java>/bin"** [COLOR=Red]**-maxdepth 1**[/COLOR]

***~~~ output ~~~***

/opt/java/<current_java>/[COLOR=Red]**bin**[/COLOR]
/opt/java/<current_java>/bin/java0
/opt/java/<current_java>/bin/java1
/opt/java/<current_java>/bin/java2
/opt/java/<current_java>/bin/java3
/opt/java/<current_java>/bin/java
/opt/java/<current_java>/bin/**[COLOR=Red]JAVAMA[/COLOR]**

```That did it. Next, since we don't want to have any directories in our list, we can restrict the **[COLOR=Blue]find[/COLOR]** command to list the type of items in its output to being only files. We do that by adding our third option ([COLOR=Green]**-type f**[/COLOR]) to our **[COLOR=Blue]find[/COLOR]** command and we finally end up with a stream of data that we will pipe into our [COLOR=Blue]**sed**[/COLOR] command later. Here it is:
```

**[COLOR=Blue]find[/COLOR] ****"/opt/java/<current_java>/bin"** [COLOR=Red]**-maxdepth 1**[/COLOR] [COLOR=Green]**-type f**[/COLOR]
 
***~~~ output ~~~***
 
/opt/java/<current_java>/bin/java0
/opt/java/<current_java>/bin/java1
/opt/java/<current_java>/bin/java2
/opt/java/<current_java>/bin/java3
/opt/java/<current_java>/bin/java

```Now we need to take a look at the **[COLOR=Blue]sed[/COLOR]** command.
[/INDENT][/INDENT]
[LIST]
[*]The **[COLOR=Blue]sed[/COLOR]** command: invokes a stream editor for filtering and transforming text. We can use this to modify the list that we got from our **[COLOR=Blue]find[/COLOR]** command. Ultimately, we'd like to remove the paths to the files in the list so that we end up with only the names of the files. So let's learn a little bit about the **[COLOR=Blue]sed[/COLOR]** command before we examine ours.
[/LIST]
[INDENT][INDENT][SIZE=2][COLOR=Blue]**sed**[/COLOR]  '**[COLOR=Green]s[/COLOR]**[COLOR=Red]**/**[/COLOR]**existing_string**[COLOR=Red]**/**[/COLOR]**replacement_string**[COLOR=Red]**/[COLOR=Green]g[/COLOR]**[/COLOR]'
[/SIZE] 
Here, **[COLOR=Blue]sed[/COLOR]** invokes the stream editor. In this example, [COLOR=Green]**s**[/COLOR] tells it that we intend to make a substitution. Specifically, we are telling it to replace the text: **existing_string** with the text: **replacement_string**. Notice the red forward slashes (**[COLOR=Red]/[/COLOR]**). They are the delineators that separate the command parameters from each other. This syntax starts with **[COLOR=Green]s[/COLOR]** which is the substitution command mentioned earlier. On the right side of the first delineator we tell **[COLOR=Blue]sed[/COLOR]** what we want it to find. On the right side of the second delineator we tell **[COLOR=Blue]sed[/COLOR]** what we want it to use as a substitution for what we've told it to find. And finally, to the right of the third delineator, there is a [COLOR=Green]**g**[/COLOR] that tells **[COLOR=Blue]sed[/COLOR]** that we want it to execute the substitution globally. Or, in other words, to make the substitution every time it finds what we've told it to look for. If we don't specify the global ([COLOR=Green]**g**[/COLOR]) option, **[COLOR=Blue]sed[/COLOR]** will only act on the first instance of its find.

Let's suppose that we want **[COLOR=Blue]sed[/COLOR]** to find something in the stream of data that we send to it, and remove every occurrence it finds. To do that, all we have to do is place the second and third delineators right next to each other so that there's nothing in between them as follows:

[SIZE=2][COLOR=Blue]**sed**[/COLOR]  '**[COLOR=Green]s[/COLOR]**[COLOR=Red]**/**[/COLOR]**existing_string**[COLOR=Red]**/**[/COLOR][COLOR=Red]**/[COLOR=Green]g[/COLOR]**[/COLOR]'[/SIZE]

The command above will remove every instance of the text: **existing_string** in the data stream.

In the data stream output from our **[COLOR=Blue]find[/COLOR]** command, we want to remove every instance of the text: **/opt/java/<current_java>/bin/** Simple. No problem, right? So let's start  building our [COLOR=Blue]**sed**[/COLOR] command and see what happens.

[SIZE=2][COLOR=Blue]**sed**[/COLOR]  '**[COLOR=Green]s[/COLOR]**[COLOR=Red]**/**[/COLOR][/SIZE]**[SIZE=2]/opt/java/<current_java>/bin/[/SIZE]**[SIZE=2][COLOR=Red]**/**[/COLOR][COLOR=Red]**/[COLOR=Green]g[/COLOR]**[/COLOR]'[/SIZE]

Uh oh...What a mess. Let's see here, the text we just told **[COLOR=Blue]sed[/COLOR]** to find is not what we intended. There isn't anything between the first and second forward slashes, and that is where **[COLOR=Blue]sed[/COLOR]** is going to expect to find the text we want it to look for. Not only that, but instead of having nothing between the second and third forward slashes, we have: **opt**. So, this command is totally hosed, and for a whole bunch of other reasons than what was just mentioned. The whole problem here is that the forward slash character (/) is used as delineators in the **[COLOR=Blue]sed[/COLOR]** command as well as delineators between directory names in the paths to the files in our list.

In order to tell **[COLOR=Blue]sed[/COLOR]** to interpret our directory delineators literally, we need to escape them so that **[COLOR=Blue]sed[/COLOR]** won't try to interpret them as its own command delineators. We escape them by placing the **[COLOR=Blue]sed[/COLOR]** escape character to the left of each forward slash in the text we want **[COLOR=Blue]sed[/COLOR]** to find. The **[COLOR=Blue]sed[/COLOR]** escape character is the backslash (\). So, instead of telling **[COLOR=Blue]sed[/COLOR]** that we want it to find this:

**[SIZE=2]/opt/java/<current_java>/bin/[/SIZE]**

We need to tell it to find this:

**[SIZE=2][COLOR=Green]\[/COLOR][/SIZE][SIZE=2]/opt[/SIZE]****[SIZE=2][COLOR=Green]\[/COLOR][/SIZE]****[SIZE=2]/java[/SIZE]****[SIZE=2][COLOR=Green]\[/COLOR][/SIZE]****[SIZE=2]/<current_java>[/SIZE]****[SIZE=2][COLOR=Green]\[/COLOR][/SIZE]****[SIZE=2]/bin[/SIZE]****[SIZE=2][COLOR=Green]\[/COLOR][/SIZE]****[SIZE=2]/[/SIZE]**

Notice the escape character ([COLOR=Green]**\**[/COLOR]) to the left of every forward slash in our path name. Now we can jam this between the first and second delineators in a **[COLOR=Blue]sed[/COLOR]** command as follows:

[SIZE=2][COLOR=Blue]**sed**[/COLOR]  '**[COLOR=Green]s[/COLOR]**[COLOR=Red]**/**[/COLOR][/SIZE]**[SIZE=2][COLOR=Green]\[/COLOR][/SIZE][SIZE=2]/opt[/SIZE]****[SIZE=2][COLOR=Green]\[/COLOR][/SIZE]****[SIZE=2]/java[/SIZE]****[SIZE=2][COLOR=Green]\[/COLOR][/SIZE]****[SIZE=2]/<current_java>[/SIZE]****[SIZE=2][COLOR=Green]\[/COLOR][/SIZE]****[SIZE=2]/bin[/SIZE]****[SIZE=2][COLOR=Green]\[/COLOR][/SIZE]****[SIZE=2]/[/SIZE]**[SIZE=2][COLOR=Red]**/**[/COLOR][COLOR=Red]**/[COLOR=Green]g[/COLOR]**[/COLOR]'[/SIZE]

Without most of the pretty colors and bolding, the command above is exactly what our orginal [COLOR=Blue]**sed**[/COLOR] command was at the beginning of this tutorial:

[SIZE=2][COLOR=Blue]**sed**[/COLOR]  's/\/opt\/java\/<current_java>\/bin\///g'
[/SIZE]
So, all we need now is to feed our [COLOR=Blue]**sed**[/COLOR] command a data stream on which it can act. We can take the output from our **[COLOR=Blue]find[/COLOR]** command, and shove it through a pipe to our [COLOR=Blue]**sed**[/COLOR] command as follows:

[SIZE=2]**[COLOR=Blue]find[/COLOR] ****"/opt/java/<current_java>/bin" [COLOR=Red]-maxdepth 1[/COLOR][COLOR=Green] -type f [COLOR=Red]| [/COLOR][/COLOR]**[/SIZE][SIZE=2][COLOR=Blue]**sed**[/COLOR]  '**[COLOR=Green]s[/COLOR]**[COLOR=Red]**/**[/COLOR][/SIZE]**[SIZE=2][COLOR=Green]\[/COLOR][/SIZE][SIZE=2]/opt[/SIZE]****[SIZE=2][COLOR=Green]\[/COLOR][/SIZE]****[SIZE=2]/java[/SIZE]****[SIZE=2][COLOR=Green]\[/COLOR][/SIZE]****[SIZE=2]/<current_java>[/SIZE]****[SIZE=2][COLOR=Green]\[/COLOR][/SIZE]****[SIZE=2]/bin[/SIZE]****[SIZE=2][COLOR=Green]\[/COLOR][/SIZE]****[SIZE=2]/[/SIZE]**[SIZE=2][COLOR=Red]**/**[/COLOR][COLOR=Red]**/[COLOR=Green]g[/COLOR]**[/COLOR]'[/SIZE] 

Let's see what it does:
```

**[COLOR=Blue]find[/COLOR] "/opt/java/<current_java>/bin" [COLOR=Red]-maxdepth 1[/COLOR][COLOR=Green] -type f [COLOR=Red]| [/COLOR][/COLOR][COLOR=Blue]sed[/COLOR] '[COLOR=Green]s[/COLOR][COLOR=Red]/[/COLOR][COLOR=Green]\[/COLOR]/opt[COLOR=Green]\[/COLOR]/java[COLOR=Green]\[/COLOR]/<current_java>[COLOR=Green]\[/COLOR]/bin[COLOR=Green]\[/COLOR]/[COLOR=Red]/[/COLOR][COLOR=Red]/[COLOR=Green]g[/COLOR][/COLOR]'**

***~~~ output ~~~***

java0
java1
java2
java3
java

```Where I live, we call results like this: paydirt!
Now we're ready to continue on to our **[COLOR=Blue]awk[/COLOR]** command.
[/INDENT][/INDENT]
[LIST]
[*]The **[COLOR=Blue]awk[/COLOR]** command: makes use of a pattern scanning and processing language named after its authors: **A**ho, ** W**einberger, and **K**ernighan. When we issue an **[COLOR=Blue]awk[/COLOR]** command, we tell the system that the statements that follow it are written in the **[COLOR=Blue]awk[/COLOR]** programming language.
[/LIST]
[INDENT][INDENT]We'll begin building our [COLOR=Blue]**awk**[/COLOR] command with something very simple like this:

[SIZE=2][COLOR=Blue]**awk**[/COLOR] '{**print**}' **[COLOR=Red]somefilename[/COLOR]**[/SIZE] 

We get output from **[COLOR=Blue]awk[/COLOR]** using its **print** statement. The **[COLOR=Blue]awk[/COLOR]** command above will output the entire contents of the input file: **[COLOR=Red]somefilename[/COLOR]**. In our case, instead of supplying the **print** statement with an input file, we'll be feeding it the data stream coming through the pipe from our **[COLOR=Blue]sed[/COLOR]** command. So, we won't need to specify a file. The following command will output everything that is piped into it.

[SIZE=2][COLOR=Blue]**awk**[/COLOR] '{**print**}'
[/SIZE]
But, we don't want all of our data all at once. We want to extract one file name from our piped list at a time. We can use the built-in **[COLOR=Blue]awk[/COLOR]** variable: **[COLOR=Green]FNR[/COLOR]**, and assign it a value of 3, to print the third line from our list as follows:

[SIZE=2][COLOR=Blue]**awk**[/COLOR] '**[COLOR=Green]FNR[/COLOR]** == 3 {**print**}'[/SIZE]

In **[COLOR=Blue]awk[/COLOR]** terms, the built-in variable **[COLOR=Green]FNR[/COLOR]** is the input [COLOR=Green]**R**[/COLOR]ecord [COLOR=Green]**N**[/COLOR]umber in the current [COLOR=Green]**F**[/COLOR]ile. Here, I'm going to employ the typical cop-out of the clueless professor and state that discovery of why the **[COLOR=Green]FNR[/COLOR]** acronym has its letters in reverse order is an exercise left to the student. In **[COLOR=Blue]awk[/COLOR]**, each line in an input file, or a piped data stream, is considered a single "input record". When we pipe the data stream from our **[COLOR=Blue]sed[/COLOR]** command into the command above, **[COLOR=Blue]awk[/COLOR]** will output its "input record number" three, which is the third line in our list of file names and contains the text: java2. We can make our **[COLOR=Blue]awk[/COLOR]** command much more flexible by using our own variable to assign a value to the built-in variable [COLOR=Green]**FNR**[/COLOR]. If we assign a value of 3 to our variable, the command shown below will give us the same output as our previous command:
[SIZE=2][COLOR=Blue][B]
awk[/B][/COLOR] **[COLOR=Red]-v[/COLOR]** [COLOR=Blue]**k**[/COLOR]=3 '**[COLOR=Green]FNR[/COLOR]** == [COLOR=Blue]**k**[/COLOR] {**print**}'[/SIZE]

Here, we have used the variable option (**[COLOR=Red]-v[/COLOR]**) to tell **[COLOR=Blue]awk[/COLOR]** that we will be assigning a value to a variable. Immediately following the **[COLOR=Red]-v[/COLOR]** option, we have chosen an arbitrary name of **[COLOR=Blue]k[/COLOR]** for our variable and assigned it a value of 3 (**[COLOR=Blue]k[/COLOR]**=3). This assignment will be made _before_ **[COLOR=Blue]awk[/COLOR]** executes the **print** statement, thereby allowing us to use our variable **[COLOR=Blue]k[/COLOR]** as the value to be assigned to the built-in variable [COLOR=Green]**FNR**[/COLOR].

Having built the command above, we now have a way to feed our **[COLOR=Blue]k[/COLOR]** variable with values from a different variable, that is external to the **[COLOR=Blue]awk[/COLOR]** programming environment, but within a shell script that contains the **[COLOR=Blue]awk[/COLOR]** command. For example, we could feed our **[COLOR=Blue]k[/COLOR]** variable with the value of a  loop counter. If we were using a counter variable named **i** we could assign its current value to our **[COLOR=Blue]k[/COLOR]** variable as follows:

[SIZE=2][COLOR=Blue]**awk**[/COLOR] **[COLOR=Red]-v[/COLOR]** [COLOR=Blue]**k**[/COLOR]=**$i** '**[COLOR=Green]FNR[/COLOR]** == [COLOR=Blue]**k**[/COLOR] {**print**}'[/SIZE]

Some might ask: Wouldn't it be easier to just do the following instead?:

[SIZE=2][COLOR=Blue]**awk**[/COLOR] '**[COLOR=Green]FNR[/COLOR]** == **$i** {**print**}'[/SIZE]

This will not work because it tells **[COLOR=Blue]awk[/COLOR]** to execute a print statement containing a variable that hasn't been assigned a value in the **[COLOR=Blue]awk[/COLOR]** environment. Remember, **[COLOR=Blue]awk[/COLOR]** is a programming language unto itself. Consequently, its statements are not knitted into the shell as seamlessly as the UNIX commands are.

[/INDENT][/INDENT]

---

### Post by noorez on 2010-11-13
wow... that's quite cool. thanks for the explanation! Sorry I haven't been able to try the new script yet. I've been having some issues with my computer but I'll fix it as soon as I can.

---

### Post by noorez on 2010-11-17
Hey...

sorry i've been away for a while.

After the latest test, it turns out that we do need to have everything packed into one command for it to work properly. There might still be a way to do separate commands but i'll have to look into it

---

### Post by Crusty Old Fart on 2010-11-17
I just noticed that **[COLOR=Blue]noorez_[/COLOR]****[COLOR=Blue]testv3.sh[/COLOR]** is generating a unary operator error that I hadn't noticed before. It happens when the last file in the list of filenames coming out of the find pipeline is the master link name: java. In fact, I think this corner case could generate errors in every version I've written so far. I'm working on the fix now.

Sorry if this has thrown a wrench into your testing.

---

### Post by noorez on 2010-11-18
in your fix...can u include this change:

MSTR_LINK = /usr/bin/java
MSTR_NAME= java
MSTR_PATH=/usr/java/jdk1.6.0_22/bin/java

i don't think u have MSTR_LINK correct. it should be /usr/bin/java as this creates a shortcut to the java executable from /usr/bin/java to /usr/java/jdk1.6.0_22/bin/java.


so the command would come out as:

update-alternatives /usr/bin/java java /usr/java/jdk1.6.0_22/bin/java 200000 --slave ...

so all slaves should be:

--slave /usr/bin/* * /usr/java/jdk1.6.0_22/bin/*

---

### Post by Crusty Old Fart on 2010-11-18
> **noorez said:**
> in your fix...can u include this change:

MSTR_LINK = /usr/bin/java
MSTR_NAME= java
MSTR_PATH=/usr/java/jdk1.6.0_22/bin/java

i don't think u have MSTR_LINK correct. it should be /usr/bin/java as this creates a shortcut to the java executable from /usr/bin/java to /usr/java/jdk1.6.0_22/bin/java.


so the command would come out as:

update-alternatives /usr/bin/java java /usr/java/jdk1.6.0_22/bin/java 200000 --slave ...

so all slaves should be:

--slave /usr/bin/* * /usr/java/jdk1.6.0_22/bin/*
Okay I made all of those changes exactly as you indicated except for the update-alternatives command. I'm assuming (always dangerous) that you intended to keep the **[COLOR=Blue]--install[/COLOR]**[COLOR=Blue][COLOR=Black] option. So, when I run the script now, that part of the output looks like this:
```

update-alternatives **[COLOR=Blue]--install[/COLOR]** /usr/bin/java java /usr/java/jdk1.6.0_22/bin/java 200000 --slave ...

```[B][COLOR=Red]Should I have omitted the [COLOR=Blue]--install[/COLOR] option?
[/COLOR][/B] 
The problem that was causing the [/COLOR][/COLOR] unary operator error has been fixed.

The script still runs in test mode.

It concatenates all the --slave options to the update-alternatives command. Output on my system looks like this:
```

update-alternatives --install /usr/bin/java java /usr/java/jdk1.6.0_22/bin/java 200000 --slave "/usr/bin/java0" "java0" "/usr/java/jdk1.6.0_22/bin/java0" --slave "/usr/bin/java1" "java1" "/usr/java/jdk1.6.0_22/bin/java1" --slave "/usr/bin/java2" "java2" "/usr/java/jdk1.6.0_22/bin/java2" --slave "/usr/bin/java3" "java3" "/usr/java/jdk1.6.0_22/bin/java3"

```**[COLOR=Red]The master side of the command has never been whitespace tolerant. I think we should make it more robust by changing the code so that it could tolerate spaces in the directory paths, but you've never indicated you wanted that so I'll leave it up to you. Please let me know if you'd like me to change it.[/COLOR]**

The new version is attached as **[COLOR=Blue]noorez_testv4.sh[/COLOR]** and its source is shown in the following code box:
```

#!/bin/bash 
  set -e  #<--Abort script immediately on error.
# set -x  #<--Turn debug tracer on.

#######################################################
# noorez_testv4.sh written by Crusty Old Fart         #
#######################################################
#      TOP OF PARAMETER CONFIGURATION SECTION         #
#######################################################

# =====================================================
# MASTER LINK CONFIGURATION:
# =====================================================

# -----------------------------------------------------
# Generic name for the master link:
#   Syntax example:
#     MSTR_LINK="/dir1/dir2/javalink" 
# -----------------------------------------------------
      MSTR_LINK="/usr/bin/java" 

# -----------------------------------------------------
# Symlink name in the alternatives directory:
#   Syntax example:
#     MSTR_NAME="javalink" 
# -----------------------------------------------------
      MSTR_NAME="java"

# -----------------------------------------------------
# The alternative being introduced for the master link:
#   Syntax example:
#     MSTR_PATH="/dir1/dir2/dir3/dir4/javalink"
# -----------------------------------------------------
      MSTR_PATH="/usr/java/jdk1.6.0_22/bin/java"

# -----------------------------------------------------
# Priority:
#   Syntax example:
#     PRIORITY=1419
# -----------------------------------------------------
      PRIORITY=200000

# =====================================================
# SLAVE CONFIGURATION:
# =====================================================

# -----------------------------------------------------
# Generic name for the slave link directory:
#   Syntax example:
#     SLV_LINK_DIR="/dir1/dir2/"
# -----------------------------------------------------
      SLV_LINK_DIR="/usr/bin/"

# -----------------------------------------------------
# Symlink name in the alternatives directory:
# -----------------------------------------------------
#  ~~~ THIS PARAMETER IS GENERATED BY THE SCRIPT ~~~ 

# -----------------------------------------------------
# The alternative path for the slave link directory:
#   Syntax example:
#     SLV_PATH_DIR="/dir1/dir2/dir3/dir4/"
# -----------------------------------------------------
      SLV_PATH_DIR="/usr/java/jdk1.6.0_22/bin/"

#######################################################
#      BOTTOM OF PARAMETER CONFIGURATION SECTION      #
#######################################################

echo -e "\n\n*********************************************"
echo "*   This script is running in test mode.    *"
echo "* No changes are being made to your system. *"
echo -e "*********************************************\n\n"

# =================
# Define functions.
# =================
function get_fname()
{
echo "$(find "$SLV_PATH_DIR" -maxdepth 1 -type f | \
        sed "s/$(echo $SLV_PATH_DIR | sed 's/\//\\\//g')//g" | \
        awk -v k=$1 'FNR == k {print}')"
}

# =====================
# Initialize variables.
# =====================
INITCMD="update-alternatives --install $MSTR_LINK $MSTR_NAME $MSTR_PATH $PRIORITY " 

# ==================================================================================================
# Determine the number of files in the target directory excluding subdirectories and their contents.
# ==================================================================================================
FILETOT="$(find "$SLV_PATH_DIR" -maxdepth 1 -type f | wc -l)"

# ==================
# Construct command.
# ==================
i=1
while [ $i -le $FILETOT ]; do 
  FNAME="$(get_fname $i)"

  # ==============================================
  # Trap and exclude the masterlink filename: java
  # ==============================================
  while [ "$FNAME" == java ]; do
    i=$[$i + 1]
    if [ $i -le $FILETOT ]; then 
      FNAME="$(get_fname $i)"
    fi
    break
  done 

  # ====================
  # Concatenate command.
  # ====================
  CATCMD="$(echo -e " --slave \"$SLV_LINK_DIR"$FNAME"\"" "\"$FNAME\"" "\"$SLV_PATH_DIR"$FNAME"\"")" 
  UPDTCMD="$(echo $UPDTCMD$CATCMD)"
  i=$[$i + 1]
done

  # ==========================================
  # Dump command construction result to shell.
  # ==========================================
  echo "$INITCMD$UPDTCMD"

echo -e "\n\n*****************"
echo "* All finished. *"
echo -e "*****************\n\n"
exit 0

```

---

### Post by noorez on 2010-11-25
Hey,

the new version appears to be working great! I'm just going to run a few tests to make sure it went well. I would like to make some additions to the script to make a little more complete if that's okay with you.

---

### Post by Crusty Old Fart on 2010-11-25
> **noorez said:**
> Hey,

the new version appears to be working great! I'm just going to run a few tests to make sure it went well. I would like to make some additions to the script to make a little more complete if that's okay with you.
Oh yeah...we can make any changes/additions you'd like. I have a few that I've been considering as well, but I've been holding them back until we get the basic script working well. We may end up with two versions -- a non-interactive version that could be run as a cron job, and perhaps another version that is interactive. I've also been considering a option that will allow it to be run in "test" mode, like it runs now, and another that runs in command mode, whereby running the script will perform the update instead of just printing commands to the screen. I'll wait to read the additions you have in mind before coding the next version. Hope you're having a good Thanksgiving.

---

### Post by noorez on 2010-11-28
Hey,

So I've been doing some readings on creating debian packages, and I think that it would be kinda cool to wrap everything that we've worked on in to a nice little package that supports install/uninstall. 

Since I really don't like the sun-java6 on the repository, I might just end up using my own build of it.

I'll let you know what other scripts we might need for this if you are still interested

---

### Post by Crusty Old Fart on 2010-11-30
> **noorez said:**
> Hey,

So I've been doing some readings on creating debian packages, and I think that it would be kinda cool to wrap everything that we've worked on in to a nice little package that supports install/uninstall. 

Since I really don't like the sun-java6 on the repository, I might just end up using my own build of it.

I'll let you know what other scripts we might need for this if you are still interested

Okay...I'm still interested. But, I don't know jack about creating debian packages. Maybe that won't end up being too much of a hindrance. After all, I didn't know jack about "update-alternatives" when we started this project, but with your help, managed to write a piece of code that worked for it. I reckon we'll see how the next phase goes.

In the meantime, I'm putting some final touches on the script and will upload it when it's ready.

---

### Post by noorez on 2010-12-07
Hey,

Sorry for the long time no post. I am still interested in this however it is currently exam season. So soon as they are done I'll start back in on this.

---

### Post by Crusty Old Fart on 2010-12-08
> **noorez said:**
> Hey,

Sorry for the long time no post. I am still interested in this however it is currently exam season. So soon as they are done I'll start back in on this.

No problem. Sounds like you have your priorities in the right order. Good luck on your exams.

---

### Post by noorez on 2010-12-30
Hey, 

I am now able to start back on this mini project of ours.

In an earlier post, you mentioned that you were working on some patches to the script. I was wondering if had those done yet? I am currently working on learning how to create debian packages so that we can make an nice installer.

---

### Post by Crusty Old Fart on 2010-12-30
> **noorez said:**
> Hey, 

I am now able to start back on this mini project of ours.

In an earlier post, you mentioned that you were working on some patches to the script. I was wondering if had those done yet? I am currently working on learning how to create debian packages so that we can make an nice installer.
Well, I _was_ working on a few things to make it somewhat interactive, and perhaps give it some options that could be specified at run time, similar to many shell commands, but when you mentioned making it into a debian package, I thought that much of what I may have changed would have been a waste of time. I reckon I should perhaps learn about debian packages, because right now, I just don't have any knowledge, understanding, or appreciation for the benefits of the debian deal or where you're trying to go with this.

Since you have been wading into the debian waters already, can you post some links to some of the better resources you've discovered?

Hope you aced all your exams and had a Merry Christmas.

Happy New Year,

Crusty

---

### Post by noorez on 2011-01-14
Hey, its time to test the debian package that I've been working on. How do we get the script that you have built to run for real and not in test mode?
Can you provide one that does this?

---

### Post by Crusty Old Fart on 2011-01-14
> **noorez said:**
> Hey, its time to test the debian package that I've been working on. How do we get the script that you have built to run for real and not in test mode?
Can you provide one that does this?
Yes...I've been working on the script tonight and have made several changes that I'm still testing. It's much better. I hope to release version 5 later tonight. I'm almost finished testing. In the meantime, I'd like you to choose a name for the script and let me know what it is. I'm also writing code that will allow it to run the commands instead of just printing them to the terminal. I think a good way to do that would be to include something like an auto run option. For example:
```

noorez -auto

```would make it issue the commands.

Whereas:
```

noorez

```would run it in test mode that only prints the commands to the shell.

On the other hand, if you'd rather have no option run the commands, then we could make it run with this:
```

noorez

```and invoke test mode with something like this:
```

noorez -test

```So, what kind of option scheme would you like, and what would you like the file to be named?

---

### Post by Crusty Old Fart on 2011-01-14
Howdy Noo:

I'm putting up noorez_v5.sh. It has the following changes:

[LIST]
[*]The entire command is now whitespace tolerant. If you have any whitespaces in your configuration parameters, be sure to enclose them in quotes, as shown in the syntax examples in the parameter configuration section of the script.
[*]All upper case local variable names have been changed to lower case to prevent the script from re-assigning a built-in bash system environment variable. I should have never used upper case letters in the first place. It's bad programming practice.
[*]The script has been condensed. It is more efficient and contains a smaller amount of code now.
[*]It can be run in test mode or auto-command mode. Test mode will not make any changes to your computer. It only sends text output to the shell. The output sends a message notification that the script is running in test mode and tells you how to run it in auto-command mode. Then it echos the command it has built. Finally, it sends a message that the script has finished running. Test mode is invoked using the following command:
[/LIST]
[INDENT]```

noorez_v5.sh

```[/INDENT]
[LIST]
[*]Auto-command mode will run the update-alternatives command that has been built by the script. It will not send any output to your shell, unless you make an error that it doesn't like after you've modified the parameter configuration section. Auto-command mode is invoked with -auto option. If no option is specified or any option other than the exact spelling of: -auto, the script will run in test mode. The following command invokes auto-command mode:
[/LIST]
[INDENT]```

noorez_v5.sh -auto

```[/INDENT]
[LIST]
[*]You can name the script whatever you like and the -auto option will work with it regardless of what you name it, providing you don't modify the code that checks the option.
[/LIST]
I recommend you run it in test mode before you run it in auto mode. I made a lot of changes and they seemed to test okay on my machine, but that doesn't necessarily mean they'll work for yours. So, please be careful and check the test results before invoking auto mode.

The new version is in the code box below as well as included as an uploaded file to this post.
```

#!/bin/bash 
  set -e  #<--Abort script immediately on error.
# set -x  #<--Turn debug tracer on.

#######################################################
# noorez_v5.sh written by Crusty Old Fart             #
#######################################################
#    BEGINNING OF PARAMETER CONFIGURATION SECTION     #
#######################################################

# =====================================================
# MASTER LINK CONFIGURATION:
# =====================================================

# -----------------------------------------------------
# Generic name for the master link:
#   Syntax example:
#     mstr_link="/dir1/dir2/javalink" 
# -----------------------------------------------------
      mstr_link="/usr/bin/java" 

# -----------------------------------------------------
# Symlink name in the alternatives directory:
#   Syntax example:
#     mstr_name="javalink" 
# -----------------------------------------------------
      mstr_name="java"

# -----------------------------------------------------
# The alternative being introduced for the master link:
#   Syntax example:
#     mstr_path="/dir1/dir2/dir3/dir4/javalink"
# -----------------------------------------------------
      mstr_path="/usr/java/jdk1.6.0_22/bin/java"

# -----------------------------------------------------
# Priority:
#   Syntax example:
#     priority=1419
# -----------------------------------------------------
      priority=200000

# =====================================================
# SLAVE CONFIGURATION:
# =====================================================

# -----------------------------------------------------
# Generic name for the slave link directory:
#   Syntax example:
#     slv_link_dir="/dir1/dir2/"
# -----------------------------------------------------
      slv_link_dir="/usr/bin/"

# -----------------------------------------------------
# Symlink name in the alternatives directory:
# -----------------------------------------------------
#  ~~~ THIS PARAMETER IS GENERATED BY THE SCRIPT ~~~ 

# -----------------------------------------------------
# The alternative path for the slave link directory:
#   Syntax example:
#     slv_path_dir="/dir1/dir2/dir3/dir4/"
# -----------------------------------------------------
      slv_path_dir="/usr/java/jdk1.6.0_22/bin/"

#######################################################
#        END OF PARAMETER CONFIGURATION SECTION       #
#######################################################

# *********************
# Initialize variables.
# *********************
  installcmd="update-alternatives --install \"$mstr_link\" \"$mstr_name\" \"$mstr_path\" $priority " 
  imax=$(find "$slv_path_dir" -maxdepth 1 -type f | sed -e 's/\/.\+\///g' -e '/^java$/ d' | wc -l)

# ********************************************
# Build update-alternatives --install command.
# ********************************************
  for (( i = 1; i <= $imax; ++i )); do 
    j="$(find "$slv_path_dir" -maxdepth 1 -type f | \
      sed -e 's/\/.\+\///g' -e '/^java$/ d' | \
      awk -v k=$i 'FNR == k {print}')"
    slavecmd="$(echo -e " --slave \"$slv_link_dir"$j"\"" "\"$j\"" "\"$slv_path_dir"$j"\"")" 
    installcmd="$(echo $installcmd$slavecmd)"
  done

# ************************************************
# Check option for test mode or auto-command mode.
# ************************************************
  if [[ $1 == -auto ]]; then
    $installcmd
  else
    echo -e "\n\n*********************************************"
    echo "* This script is running in test mode.      *"
    echo "* No changes are being made to your system. *"
    echo "*                                           *"
    echo "* To run the update-alternatives command,   *"
    echo "* invoke this script with the -auto option  *"
    echo -e "*********************************************\n\n"
    echo $installcmd
    echo -e "\n\n*****************"
    echo "* All finished. *"
    echo -e "*****************\n\n"
  fi
exit 0


```I'm curious to know how it works out for you and will be happy to make any changes you want.

Good luck,

Crusty

---

### Post by noorez on 2011-02-10
Hey, 

from what I've tested, it seems to work fine but i'm going to do a little bit more just in case something goes wrong.

if this one does work, we can make one more addition. it will probably be easy as we just have to slave a couple more things to the java link (in this case it would be the man pages of the java binary files)

---

### Post by Crusty Old Fart on 2011-02-12
So far, so good, eh? Thanks for letting me know. Hopefully, further testing will continue to show success and we can slave the man pages soon.

---

