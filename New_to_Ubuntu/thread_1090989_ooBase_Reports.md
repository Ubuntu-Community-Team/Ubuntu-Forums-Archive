---
title: "ooBase Reports"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by acreech on 2009-03-08
I am attempting to build a database with OpenOffice and have ran into a minor road block. I do not have alot of experience with databases so this is probably my lack of knowledge on the subject. 

I have a database built that will record donors, dates of Donations and amount donated. I would like to create a report that will sort the data base by year, then donor. Then I want it to total up all their donations. 

My table has these columns.......Account, Designation, Name, Transaction Number (Primary Key, Auto Number), Amount, etc.... there are a few other columns that are insignificant. 

How do I make a report that sort my entries by year, then name and finally total up all donations?


Any help would be appreciated.

thanks 
acreech

---

### Post by Siph0n on 2009-03-08
With just one table, why not just do a spreadsheet? OpenOffice has one, and it can sort, and add up columns really easily...

---

### Post by acreech on 2009-03-08
The person who actually tracks this information does have it in a spreadsheet right now, but they would rather have it in a database for the capabilities of the reports. There was a previous database made in Microsoft Access that did track these donations, however that database was lost when the person's computer crashed. The previous database did these things. I don't have microsoft anymore (at all), so I am just trying to re-create the database for them in openoffice.

I think that OO has the ability to do what I want, I just don't know how to make it do it.

---

### Post by acreech on 2009-03-10
Bump

---

### Post by bonzini on 2009-03-10
So have you tried clicking on the "Report" icon in OOBase and selecting the wizard?

> **acreech said:**
> Bump

---

### Post by acreech on 2009-03-11
The Wizard only lets you put fields that are in your table or query into the report. It does not give you options for totalling the amounts. If it does let you total the amounts, then I don't recognize the option for that.

---

### Post by acreech on 2009-03-11
> **acreech said:**
> The Wizard only lets you put fields that are in your table or query into the report. It does not give you options for totalling the amounts. If it does let you total the amounts, then I don't recognize the option for that.

I finally found the answser that I was looking for. here is the link and the info...... http:// [www.oooforum.org/forum/viewtopic.phtml?t=71850](www.oooforum.org/forum/viewtopic.phtml?t=71850)

"Let me attempt to WALK you through the process of setting up your query . . . using . . . GROUP and SUM functions.

I am assuming based on your question, that you are using HSQL as the embedded database ( you are asking this question in the Base forum, not in Calc ) . . . and . . . you have a 'table' that includes fields named productID and Quantity .

Therefore, you can create a Query to accomplish what you want. The steps I would follow to create this Query would be:

   1. Open your database in OpenOffice
   2. On the left, under Database, click on Queries
   3. Under Tasks, click on Create Query in Design View...
   4. An Add Table or Query box will appear, click on your Table name, press the Add button
   5. In the row labeled Field, click on your field name . . . productID
   6. In the row labeled Function, click on Group
   7. In the next column in the row labeled Field, click on your field name . . . Quantity
   8. In the row labeled Alias, give the column a name of your choice, for example: Total Quantity
   9. In the row labeled Function, click on Sum
  10. Run your query by pressing on the Run Query Icon, OR, from the Menu: Edit - Run Query, OR, press F5
  11. Save the Query, if you desire by pressing the Save Icon, OR, from the Menu: File - Save, OR, press Ctrl+S"

---

