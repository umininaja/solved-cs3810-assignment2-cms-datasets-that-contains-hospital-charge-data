Download Link: https://assignmentchef.com/product/solved-cs3810-assignment2-cms-datasets-that-contains-hospital-charge-data
<br>
The Centers for Medicare and Medicaid Services is a U.S. agency that administers the Medicare program and works in partnership with state governments to administer Medicaid.  CMS makes health related data available to the public through its website <a href="https://data.cms.gov/">data.cms.gov</a>.  In this assignment you will use one of CMS’ datasets that contains hospital charge data, referred to as IPPS dataset<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>and available <a href="https://data.cms.gov/Medicare-Inpatient/Inpatient-Prospective-Payment-System-IPPS-Provider/97k6-zzx3">here</a>.  The IPPS dataset contains information about 2017 charges of top 100 groups of similar clinical conditions (diagnosis) by different health providers in the U.S. and the correspondent amounts covered by health insurance.  The “IPPS dataset” shows how the same treatment for a clinical condition can result in very different costs for the patients depending on the health care provider.

<h1><strong>2. Data Model</strong></h1>

The “IPPS dataset” has 163K rows and 12 columns.  The goal of this assignment is to have you download this dataset in a CSV format so you can later load all of its data content into a MySQL database named ipps.  The ipps database has to be designed so that all of its tables are normalized up to 3NF (third normal form).  All Data Definition Language (DDL) SQL statements (CREATE DATABASE and CREATE TABLE statements) and DCL (Data Control Language) statements (CREATE USER, GRANT statements) should be submitted in a file named ipps.sql.  In summary, all ipps’s tables of your database should be normalized up to 3NF, have primary keys, and appropriate foreign keys with referential integrity constraints in place. You should also create a user named ipps with full control of all tables in the ipps database.

<h1><strong>3. Data Load</strong></h1>

In order to load the “IPPS dataset” CSV file into your MySQL database you will have to write a data load program (preferable languages are Python or Java).  This program should be named ipps.[py|java] (extension depends on the programming language of your choice) and it is the second deliverable of this assignment.  Use the examples described in the MySQL connector resources (available <a href="https://sites.google.com/view/thyagomota/courses/19fcs3810/19fcs3810-resources">here</a>) to help you write the data load program. You may find the following csvSplit function (in Python) useful when splitting the lines from the CSV file by comma into an array of data fields. csvSplit ignores commas when they appear inside a string.

<table width="624">

 <tbody>

  <tr>

   <td width="624"># split by comma function that avoids splitting when commas appear within a stringdef csvSplit(line):data = []while True:s = ”inString = Falsefor c in line:line = line[1:]if c == ‘”‘:inString = not inStringcontinueif not inString and c == ‘,’:breakelse:s += cif len(s) == 0:breakdata.append(s)return data</td>

  </tr>

 </tbody>

</table>




<table width="624">

 <tbody>

  <tr>

   <td width="624">// csvSplit implementation in Java<strong>public static </strong>String[] csvSplit(String line) {ArrayList&lt;String&gt; data = <strong>new </strong>ArrayList&lt;String&gt;();<strong>char </strong>chars[] = line.toCharArray();<strong>int </strong>i = 0;<strong>while </strong>(<strong>true</strong>) {String s = <strong>“”</strong>;<strong>boolean </strong>inString = <strong>false</strong>;<strong>for </strong>(; i &lt; chars.<strong>length</strong>; i++) {<strong>char </strong>c = chars[i];<strong>if </strong>(c == <strong>‘”‘</strong>) {inString = !inString;<strong>continue</strong>;}<strong>if </strong>(!inString &amp;&amp; c == <strong>‘,’</strong>) {i++;<strong>break</strong>;}<strong>else</strong><strong>               </strong>s += c;}<strong>if </strong>(s.length() == 0)<strong>break</strong>;data.add(s);}String template[] = <strong>new </strong>String[1];<strong>return </strong>data.toArray(template);}</td>

  </tr>

 </tbody>

</table>




Please note that <strong>you are not allowed to pre-process the CSV file</strong> other than using your ipps data load program.  For example, you cannot manually pre-process the CSV file using a spreadsheet application.  I will test your data load program using the CSV file obtained directly from data.cms.gov’s download – CSV option. The CSV file should be renamed to ipps.csv. Because this file is large (26.8MB) and it can be downloaded from the internet, there is no need to submit it through blackboard.

<a href="#_ftnref1" name="_ftn1"><sup>[1]</sup></a> “Inpatient Prospective Payment System (IPPS) Provider Summary for the Top 100 Diagnosis-Related Groups (DRG).”