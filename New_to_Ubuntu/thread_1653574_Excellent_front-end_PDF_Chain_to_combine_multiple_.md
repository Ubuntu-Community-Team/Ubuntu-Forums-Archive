---
title: "Excellent front-end PDF Chain to combine multiple PDF files"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by shuttleworthwannabe on 2010-12-27
Here is the link to the home page: [http://pdfchain.sourceforge.net/](http://pdfchain.sourceforge.net/)
It is in repo's, and find it in Office menu; the rest is as easy as point-n-click. Enjoy!

S:popcorn:

---

### Post by karthick87 on 2010-12-27
You can also try,pdfshuffler
```
sudo apt-get install pdfshuffler 
```

---

### Post by MondoTofu on 2011-04-20
Ya!  pdfshuffler helped me grab pages from different pdf sources and combine them into a third without disrupting the originals.

The GUI is simple, direct, and doesn't require explanation.  Very rare for a program these days.

---

### Post by shuttleworthwannabe on 2011-04-21
Great--will give the shuffler a try.

---

### Post by theemahn on 2012-12-23
```
#!/bin/bash
###########################################################
##                     Mergepdf Tool                     ##     
## Created by TheeMahn: <theemahn@ultimateedition.info>  ##
## Licensed under GNU GPL v3 or later, at your option.   ##
##       http://www.gnu.org/licenses/gpl.html            ##
###########################################################
#
# Mergepdf is a part of the tm-tools package.
# Many of the tools are heavy and are not
# intended to be ran by the common user.  
# The tools are typically geared for the admininstrator.
# please see man tmtools for more info.
#
# http://ultimateedition.info
MERGEPDF="1.7.1-6"
# set colors so errors etc. stand out.

txtblk='\e[0;30m' # Black - Regular
txtred='\e[0;31m' # Red
txtgrn='\e[0;32m' # Green
txtylw='\e[0;33m' # Yellow
txtblu='\e[0;34m' # Blue
txtpur='\e[0;35m' # Purple
txtcyn='\e[0;36m' # Cyan
txtwht='\e[0;37m' # White
bldblk='\e[1;30m' # Black - Bold
bldred='\e[1;31m' # Red
bldgrn='\e[1;32m' # Green
bldylw='\e[1;33m' # Yellow
bldblu='\e[1;34m' # Blue
bldpur='\e[1;35m' # Purple
bldcyn='\e[1;36m' # Cyan
bldwht='\e[1;37m' # White
unkblk='\e[4;30m' # Black - Underline
undred='\e[4;31m' # Red
undgrn='\e[4;32m' # Green
undylw='\e[4;33m' # Yellow
undblu='\e[4;34m' # Blue
undpur='\e[4;35m' # Purple
undcyn='\e[4;36m' # Cyan
undwht='\e[4;37m' # White
bakblk='\e[40m'   # Black - Background
bakred='\e[41m'   # Red
badgrn='\e[42m'   # Green
bakylw='\e[43m'   # Yellow
bakblu='\e[44m'   # Blue
bakpur='\e[45m'   # Purple
bakcyn='\e[46m'   # Cyan
bakwht='\e[47m'   # White
txtrst='\e[0m'    # Text Reset
function Help {
	echo -e "${txtwht}

PDFMerge $VERSION
==============

PDFMerge is a part of the tm-tools package.  Many of the tools are heavy and are not
intended to be ran by the common user.  The tools are geared for the admininstrator.
please see man tmtools for more info.

PDFMerge -<OUTFILE>

	possible commands...
	-o	--output		PDF file to write
	-m	--metadata		update metadata from filename.
	-v	--version		dump version info
	-h	--help			this help message

	Useage Output;
	pdfmerge -o merged.pdf

	Will process all files in current folder merging them into one pdf.

	Useage Metadata;

	Will stamp the title of all pdf's in current folder with current filename
	stripping underscores.

	Useage Help;
	PDFMerge -h

	Displays this message. For futher information please refer to the manpages.  

	man pdfmerge
	"
echo "
GNU PDFMerge home page: <http://www.ultimateedition.info/>.
E-mail bug reports to: <theemahn@ultimateedition.info>.
Be sure to include the word PDFMerge somewhere in the Subject: field."
	exit 0
}

function Version {
echo "PDFMerge $VERSION
==============
GNU PDFMerge home page: <http://www.ultimateedition.info/>.
E-mail bug reports to: <theemahn@ultimateedition.info>.
Be sure to include the word pdfmerge"
}

function PREPROCESS()
{
ls *.pdf > tmp.txt
cat tmp.txt | while read FILE
do
    echo $FILE
    RETVAL=$(echo $? | sed 's/0//g')

    #echo "Something to the screen..." >&2
    echo $RETVAL
  done
}

function Metadata()
{
ls *.pdf > tmp.txt
cat tmp.txt | while read FILE
do
    pdftk $FILE dump_data output $FILE.tags
#Manipulate
SFILE=${FILE%%.pdf}
TITLE=$(echo $SFILE | sed 's/_/ /g')
#To be implemented - Not used 
#sed -i "8s/InfoValue.*/InfoValue: Linux Magazine/g" $FILE.tags
sed -i "4s/InfoValue.*/InfoValue: $TITLE/g" $FILE.tags
mv $FILE TEMP.pdf
pdftk TEMP.pdf update_info $FILE.tags output $FILE
# Clean up
rm TEMP.pdf
rm $FILE.tags
    RETVAL=$(echo $? | sed 's/0//g')
    echo $RETVAL
  done
# Clean up
rm tmp.txt
}

    case "$1" in
      -h|--help|-\?) Help; exit 0;;
      -v|--version) Version; exit 0;;
      -o|--output) PDFTP=$(PREPROCESS $1); echo -e "Processing command: pdftk $PDFTP cat output $2${txtrst}"; pdftk $PDFTP cat output $2; exit 0;;
      -m|--metadata) echo -e "${bldgrn}Processing command: pdftk $FILE dump_data output $FILE.tags${txtrst}"; PDFTP=$(Metadata $1); exit 0;;
      *) Help; exit 0;;
    esac


```
Maybe someone will find this useful ;)
**Requires**: pdftk
```
sudo apt-get install pdftk
```

---

### Post by overdrank on 2012-12-23
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

