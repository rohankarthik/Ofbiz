# Using the Birt Report Designer - Admin/Super-User #
## Introduction ##
The creation of a flexible report goes through a design step of the initial flexible report output under the Birt Report Designer. 

This document describes the simplest designs to connect to the data. It is not exhaustive, and simply attempts to cover basic needs. You will find much more documentation online. In our approach, the connection to the data is generated automatically by OFBiz, only the design part of the report will be discussed.

## Installing the BIRT Report Designer ##
Installing the BIRT Report Designer is easy. If you use Eclipse, you can include it as a plugin. You can also install the whole BIRT Report Designer. I use Eclipse but I prefer the second way, to not mix things. So simply download and install the whole all-in-one thing. Or install the plugin if you prefer and use its "Report Design" view which allows to edit .rptdesign files.

>_Note_: if you installed the BIRT Report Designer under say, a Birt directory, then by default the reports will be accessed from the Birt\workspace\Report Builder directly and this is where you should put the .rptdesign files when downloading them. Your mileage may wary... 

## Different areas of the screen and their role ##
### Navigator - Report Builder ###
This is where you should find the .rptdesign files you downloaded.

![Report Builder](https://cwiki.apache.org/confluence/download/attachments/68720496/Report%20Builder.png?api=v2)

### Data Explorer ###
The Data Explorer defaults to the right of your screen. It gives you access to two things. The data fields available for the report, and the filter fields that can be used for this report.

![Data Explorer](https://cwiki.apache.org/confluence/download/attachments/68720496/Data%20Explorer.png?api=v2)

### Palette ###
The palette provides the various tools you can insert in the report. Simple text, image, table of data, layout table, graph, aggregation, etc. All objects are added to the report by drag & drop.
![Palette](https://cwiki.apache.org/confluence/download/attachments/68720496/Palette.png?api=v2)

### Tabs ###
At the right bottom of the window is a series of five tabs.

We will use two: 

- Layout, which will allow most of the design. 
- Master Page, which will give access by its owners to standard parameters such as the orientation or size of the report.

The preview is not accessible because it can not be executed outside of OFBiz. Any changes to the scripts will be erased during the upload in OFBiz.

### Simple design without break ###
The simplest possible design is to insert in a table (table in the palette), a part or all of the data set data fields. To do this, right-click on Data Set in the Data Explorer -> Insert in Layout, and then select the fields you want to see appear.

### Simple design with break ###
A break is a collection of data made by Birt from the data. It permits to classify according to a field, and to give details for each category, then to aggregate certain fields, etc.

1. Insert a table (Table) in the report -> OK
2. Right-click on the table -> Edit Data Binding, select all fields
3. In the data set field, change "None" in "Data Set", validate
4. Right-click the table -> Insert Group. Configure your group, eg: ![group](https://cwiki.apache.org/confluence/download/attachments/68720496/Group.png?api=v2)
5. Your table then has five lines:
 * A global title line
 * A title line of the group
 * A group detail line
 * A footer of the group
 * A global footer line
6. Then insert some elements in the design: in the global header, everything that does not depend on the group, for example the title of the report. In the header of the group, everything that is common to the whole group and that you want to see in its title. In the details, the fields that may appear for each group line. As in the image below, the fields might be inserted by Copy/Paste from the Data Set, and titles via a text element of the palette. You can add lines and columns by right clicking on the end of the line (gray rectangle when the table is selected), etc. ![Design with break](https://cwiki.apache.org/confluence/download/attachments/68720496/Design%20with%20break.png?api=v2)

#### Construction of aggregation ####
The aggregations may be on the whole table, or only on a group. They are characterized by an expression to aggregate (made up of different data fields), a possible filter on the data lines, and an aggregation function, eg:
![Aggregation builder](https://cwiki.apache.org/confluence/download/attachments/68720496/Aggregation%20builder.png?api=v2)
#### Expression builder ####
The *fx* (for expression and filter) buttons are used to open a complex expression construction window. It is possible to use predefined functions, Javascript, data fields, already built aggregations, and so on. This window can also be used by including a data element, which allows to construct non-aggregated data expressions.
![Expression builder](https://cwiki.apache.org/confluence/download/attachments/68720496/Expression%20builder.png?api=v2)

Footer lines often allow you to place aggregations, such as sums on the group or table rows, eg
![Design with break complete](https://cwiki.apache.org/confluence/download/attachments/68720496/Design%20with%20break%20complete.png?api=v2)

> Warning: any unused line must be deleted, otherwise it generates white spaces on the report.

## Layout Management ##
### General settings ###
Right button leads to Properties Editor tab at bottom. Then click on the Master Page tab, just above. In the Property Editor you will see a series of general properties that will allow you to modify the general form of the report.

### Styles ###
By right-clicking on any item in the table, you have access to the menu of styles. From there they can be edited, applied, created. A style can be applied to the whole picture, to a row or column, to a cell, or to an element in that cell (text, data, ...).
