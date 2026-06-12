---
title: "Map program for plotting a list of locations"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by mgough85 on 2011-01-23
I'm looking for a program that will plot a series of locations with labels on a map.

I do not want the information to be loaded on a server or anything like that as the information will be people in my church and should be confidential.

It would be great if it could print using letters and numbers on the x and y axis (Cartesian coordinate system?).  Spreadsheet entry is a plus.

Any suggestions?

---

### Post by charlie_b on 2011-01-23
To do what you want you would need to use some kind of GIS software. The only GIS I know of in the repositories is GRASS, which will undoubtedly do what you want, but has a steep learning curve. If some of the simpler GIS software is available, such as JUMP or Quantum GIS, that may be better suited to your needs.

---

### Post by Herman on 2011-02-18
:P I highly recommend Quantum GIS for that kind of work.

Quantum GIS, (or qgis for short), is available from  'Applications', 'Ubuntu Software Center' in the most recent version of Ubuntu. For older versions of Ubuntu see this thread, [**Ubuntu 10.4 LTS & Quantum GIS (QGIS) 1.4 (Ubuntu version)  **]("http://ubuntuforums.org/showthread.php?t=1470575")

An important tip for the first time you use qgis after installing it if you want to get the most value out of this wonderful program is to go 'Plugins'->'Manage Plugins', and enable the plugin called 'Plugin Installer', which gives you the opportunity to download and install more python plugins as may be required from time to time when you want to perform useful operations with qgis.

Also, you should at least enable 'Add Delimted Text Layer', in the qgis plugin manager, because I'm going to explain to you how you can use it shortly. 
You may also enable any other plugins you think you might like at any time.

To achieve spreadsheet input for Quantum GIS, you should install a spreadsheet program from 'Applications', 'Ubuntu Software Center' called 'Gnumeric Spreadsheet'.
As far as I know, Quantum GIS can't accept the data in spreadsheet form, but Quantum GIS does readily accept .csv files, and it's easy to click 'save as' in Gnumeric spreadsheet, and choose '.csv' as your file type.

A .csv file is just a plain text file which has columns separated by commas, (hence the name '.csv', (for 'comma separated values). More info: [Comma Separated Values]("http://en.wikipedia.org/wiki/Comma-separated_values") - Wikipedia.

When I last tried, Open Office .org Spreadsheet was not able to 'save  as' a .csv file that could be opened in qgis, I don't know why, but I  found out by trial and error that only Gnumeric spreadsheet made a  suitable .csv file, so we need Gnumeric speadsheet, not the Open Office  version. My advice is to actively avoid allowing your .csv files to be  opened with OOo Spreadsheet.
Gedit text editor is also extremely useful for editing .csv files.

Your first row should have column titles something like this,
```
Y_Coords_WGS84,X_Coords_WGS84,lastname,middlename,firstname,suburb,street,house_number,phone_number_1,phone_number_1
```In the rows underneath, you enter your data, (of course). You can add more colums to suit your requirements, such as 'last_visit_date' maybe or anything you like.
When finished or at any time you like, click 'save as', and make sure you select to save your spreadsheet as a .csv file type. 

Here is a sample of what some example data might look like in a csv file,
```
Y_Coords_WGS84,X_Coords_WGS84,lastname,middlename,firstname,suburb,street,house_number,phone_number_1,phone_number_1
-25.383333,131.083333,smith,robert,bradley,heath,spence_st,43,,
-20.412718,131.178031,good,rose,mary,portsmith,middle_ave,54,,
-20.577292,131.135843,wilson,joseph,paul,hogan,bucasia,12,,

```[B]How to open your .csv files in Quantum GIS
[/B]1. Open Quantum GIS, 'Applications', 'Science', 'Quantum GIS'
2.' Plugins','Delimited Text', 'Add Delimited Text Layer'
3. (i) Field 1: Delimited text file, either type the path and name of  your file, or use the browse button at the end of the field and navigate  to your .csv file and select it.
    (ii) Field 2: automatically filled from the filename of your .csv or you may optionally change it as you like
   (iii) Field 3: type a comma in the box for 'Delimiter string', and select 'Plain Characters' if that's not already set
(iv) Field 4: 'Geometry', probably will be filled automatically to  'X_Coords_WGS84' in the X field and 'Y_Coords_WGS84' in the 'Y' field,  but you can use the drop-down menus to change it if you want to for any  reason.   
(v) Click 'Okay'

Now you should see some dots in Quantum GIS and you can click on each one of those with the information tool in Quantum GIS to see the data you entered in the spreadsheet.
You can also go over to the sidebar and right-click on the new layer, and select 'Properties'. Then click on the 'Labels' icon, enable 'display labels' in the checkbox you'll find there at the top, and use the 'Field Containing Label' spinbox to set the label to be displayed as 'last_name', (or whatever you want).
There are all kinds of settings in Quantum GIS to explore and play with, I'm sure you'll have fun learning qgis yourself once you get started with it.

You will probably want some kind of a background map to give the new placemarks some meaning. See '**How to open your .csv files in Quantum GIS**' in post #4 of thie following thread, [**Re: usb gps on ubuntu. how to, maybe... **]("http://ubuntuforums.org/showthread.php?t=1430516")
Or you can load some other kind of map, whatever you can find available in your area, qgis can open map files of most kinds formats.

You can also use the database in qgis to sort and search through all your data, here's a link to a video tutorial about that, **[*QGIS 4* - Finding & Selecting Data]("http://www.google.com.au/url?sa=t&source=video&cd=1&ved=0CDQQtwIwAA&url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DZbnCrfoWnNk&rct=j&q=qgis%204&ei=0N5eTd-QFoTCca7p6acK&usg=AFQjCNGckl__IwzqNpIjZ4v1NueADPHMyg&sig2=i3D8j3Zk9_W68_3mdnhStQ&cad=rja").**

Another cool trick you can do with qgis is to right-click on your layer and choose 'save as', and set the spinbox to 'keyhole markup language', or KML, which is a google earth file. 
Type in a file name and click 'Okay'.
Open Google Earth and from the file menu, click 'Open' and browse to your new .kml file. 

Regards, Herman :P

---

### Post by Pynalysis on 2011-10-04
> **Herman said:**
> :P I highly recommend Quantum GIS for that kind of work.

Quantum GIS, (or qgis for short), is available from  'Applications', 'Ubuntu Software Center' in the most recent version of Ubuntu. For older versions of Ubuntu see this thread, [**Ubuntu 10.4 LTS & Quantum GIS (QGIS) 1.4 (Ubuntu version)  **]("http://ubuntuforums.org/showthread.php?t=1470575")

An important tip for the first time you use qgis after installing it if you want to get the most value out of this wonderful program is to go 'Plugins'->'Manage Plugins', and enable the plugin called 'Plugin Installer', which gives you the opportunity to download and install more python plugins as may be required from time to time when you want to perform useful operations with qgis.


Also, you should at least enable 'Add Delimted Text Layer', in the qgis plugin manager, because I'm going to explain to you how you can use it shortly. 
You may also enable any other plugins you think you might like at any time.

To achieve spreadsheet input for Quantum GIS, you should install a spreadsheet program from 'Applications', 'Ubuntu Software Center' called 'Gnumeric Spreadsheet'.
As far as I know, Quantum GIS can't accept the data in spreadsheet form, but Quantum GIS does readily accept .csv files, and it's easy to click 'save as' in Gnumeric spreadsheet, and choose '.csv' as your file type.

A .csv file is just a plain text file which has columns separated by commas, (hence the name '.csv', (for 'comma separated values). More info: [Comma Separated Values]("http://en.wikipedia.org/wiki/Comma-separated_values") - Wikipedia.

When I last tried, Open Office .org Spreadsheet was not able to 'save  as' a .csv file that could be opened in qgis, I don't know why, but I  found out by trial and error that only Gnumeric spreadsheet made a  suitable .csv file, so we need Gnumeric speadsheet, not the Open Office  version. My advice is to actively avoid allowing your .csv files to be  opened with OOo Spreadsheet.
Gedit text editor is also extremely useful for editing .csv files.

Your first row should have column titles something like this,
```
Y_Coords_WGS84,X_Coords_WGS84,lastname,middlename,firstname,suburb,street,house_number,phone_number_1,phone_number_1
```In the rows underneath, you enter your data, (of course). You can add more colums to suit your requirements, such as 'last_visit_date' maybe or anything you like.
When finished or at any time you like, click 'save as', and make sure you select to save your spreadsheet as a .csv file type. 

Here is a sample of what some example data might look like in a csv file,
```
Y_Coords_WGS84,X_Coords_WGS84,lastname,middlename,firstname,suburb,street,house_number,phone_number_1,phone_number_1
-25.383333,131.083333,smith,robert,bradley,heath,spence_st,43,,
-20.412718,131.178031,good,rose,mary,portsmith,middle_ave,54,,
-20.577292,131.135843,wilson,joseph,paul,hogan,bucasia,12,,

```[B]How to open your .csv files in Quantum GIS
[/B]1. Open Quantum GIS, 'Applications', 'Science', 'Quantum GIS'
2.' Plugins','Delimited Text', 'Add Delimited Text Layer'
3. (i) Field 1: Delimited text file, either type the path and name of  your file, or use the browse button at the end of the field and navigate  to your .csv file and select it.
    (ii) Field 2: automatically filled from the filename of your .csv or you may optionally change it as you like
   (iii) Field 3: type a comma in the box for 'Delimiter string', and select 'Plain Characters' if that's not already set
(iv) Field 4: 'Geometry', probably will be filled automatically to  'X_Coords_WGS84' in the X field and 'Y_Coords_WGS84' in the 'Y' field,  but you can use the drop-down menus to change it if you want to for any  reason.   
(v) Click 'Okay'

Now you should see some dots in Quantum GIS and you can click on each one of those with the information tool in Quantum GIS to see the data you entered in the spreadsheet.
You can also go over to the sidebar and right-click on the new layer, and select 'Properties'. Then click on the 'Labels' icon, enable 'display labels' in the checkbox you'll find there at the top, and use the 'Field Containing Label' spinbox to set the label to be displayed as 'last_name', (or whatever you want).
There are all kinds of settings in Quantum GIS to explore and play with, I'm sure you'll have fun learning qgis yourself once you get started with it.

You will probably want some kind of a background map to give the new placemarks some meaning. See '**How to open your .csv files in Quantum GIS**' in post #4 of thie following thread, [**Re: usb gps on ubuntu. how to, maybe... **]("http://ubuntuforums.org/showthread.php?t=1430516")
Or you can load some other kind of map, whatever you can find available in your area, qgis can open map files of most kinds formats.

You can also use the database in qgis to sort and search through all your data, here's a link to a video tutorial about that, **[*QGIS 4* - Finding & Selecting Data]("http://www.google.com.au/url?sa=t&source=video&cd=1&ved=0CDQQtwIwAA&url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DZbnCrfoWnNk&rct=j&q=qgis%204&ei=0N5eTd-QFoTCca7p6acK&usg=AFQjCNGckl__IwzqNpIjZ4v1NueADPHMyg&sig2=i3D8j3Zk9_W68_3mdnhStQ&cad=rja").**

Another cool trick you can do with qgis is to right-click on your layer and choose 'save as', and set the spinbox to 'keyhole markup language', or KML, which is a google earth file. 
Type in a file name and click 'Okay'.
Open Google Earth and from the file menu, click 'Open' and browse to your new .kml file. 

Regards, Herman :P

+1 for Quantum GIS

---

