# XML

## Introduction

- XML stands for eXtensible Markup Language
- XML tags are not predefined in XML. You must define your own tags. (And hence it is Extensible)
- XML was designed to describe, store and transport data.
- While storing it can be taken as alternative of database systems.
- XML is a markup language much like HTML
- XML was designed to be both human- and machine-readable.
- XML was designed to be self-descriptive
- XML is often used for distributing data over the Internet.
- Platform independent
- XML uses a DTD (Document Type Definition) to formally describe the data.
- XML documents are formed as element trees.

## XML vs HTML
- XML is not a replacement for HTML. XML and HTML were designed with different goals:
- XML was designed to describe data and to focus on what data is. HTML was designed to display data and to focus on how data looks.
- HTML is about displaying information, XML is about describing information.

### Example 1
```xml
<?xml version="1.0" encoding="UTF-8"?>
<note>
  <to>Tove</to>
  <from>Jani</from>
  <heading>Reminder</heading>
  <body>Don't forget me this weekend!</body>
</note>
```

### Syntax & Rules
- XML file should start with XML `Prolog` i.e. `<?xml version="1.0" encoding="UTF-8"?>`. This is optional but if added, should go on top.
- To use international/unicode characters use encoding as `UTF-8`
- All XML documents must have a root tag
- All XML elements must have a closing tag
- XML tags are case sensitive, XML tags are case sensitive. The tag `<Message>` is different from the tag `<messege>`
- All XML elements must be properly nested, `<b><i>This text is bold and italic</b></i>`
- Attribute values must always be quoted `<note date=12/11/99>`, `<note date="12/11/99">`
- Special characters should be in Entity References. Like `<` should be `&lt;`
```
&lt;	<	less than
&gt;	>	greater than
&amp;	&	ampersand 
&apos;	'	apostrophe
&quot;	"	quotation mark
```
- Comments are written like in  HTML `<!-- This is a comment -->`
- White-space is Preserved in XML

XML documents that conform to the syntax rules above are said to be "Well Formed" XML documents.


### XML Elements : 
An XML element is everything from (including) the element's start tag to (including) the element's end tag.

An element can contain:
- text
- attributes
- other elements
- or a mix of the above

#### XML Naming Rules
- Are case-sensitive
- Must start with a letter or underscore
- Cannot start with the letters xml (or XML, or Xml, etc)
- Can contain letters, digits, hyphens, underscores, and periods
- Cannot contain spaces

### Example 2
```xml
<?xml version="1.0" encoding="UTF-8"?>
<breakfast_menu>
	<food>
	    <name>Belgian Waffles</name>
	    <price>$5.95</price>
	    <description>
	   Two of our famous Belgian Waffles with plenty of real maple syrup
	   </description>
	    <calories>650</calories>
	</food>
	<food>
	    <name>Strawberry Belgian Waffles</name>
	    <price>$7.95</price>
	    <description>
	    Light Belgian waffles covered with strawberries and whipped cream
	    </description>
	    <calories>900</calories>
	</food>
	<food>
	    <name>Homestyle Breakfast</name>
	    <price>$6.95</price>
	    <description>
	    Two eggs, bacon or sausage, toast, and our ever-popular hash browns
	    </description>
	    <calories>950</calories>
	</food>
</breakfast_menu>
```

- This example contains multiple nodes i.e. repeatative data like Food menu as `<food>`


## XML Attributes
- XML attributes are normally used to describe XML elements, or to provide additional information about elements
- Attributes are always contained within the start tag of an element. `<person id="3344">`
- Use of Elements vs. Attributes `<person sex="female">` or `<person><sex>female</sex></person>`
- There are no fixed rules about when to use attributes to describe data, and when to use elements.
- Use attributes when you are sure that there won't be any repeatative values for certain data/values.

## XML Namespaces
- XML Namespaces provide a method to avoid element name conflicts.
- With prefixing a namespace with element, conflict can be avoided i.e. `<namespace:element_name>`
- A namespace has to be defined prior to use in opening element tag using `xmlns` attribute i.e. `<namespace:element_name xmlns="some_url">`

### XML Namespaces - The xmlns Attribute
- When using prefixes in XML, a namespace for the prefix must be defined.
- The namespace can be defined by an xmlns attribute in the start tag of an element.
- The namespace declaration has the following syntax. xmlns:prefix="URI".
- Namespaces can also be declared in the XML root element 
```
<root xmlns:h="http://www.w3.org/TR/html4/"
xmlns:f="https://www.w3schools.com/furniture">
```
- The purpose of using an URI is to give the namespace a unique name.
- Default Namespaces defining without name but it has to be unique
```
<table xmlns="namespaceURI">
```

## CDATA vs PCDATA
### CDATA
CDATA: (Unparsed Character data): CDATA contains the text which is not parsed further in an XML document. Tags inside the CDATA text are not treated as markup and entities will not be expanded.
```xml
<?xml version="1.0"?>  
<employee>  
<![CDATA[  
  <firstname>vimal</firstname> 
  <lastname>jaiswal</lastname> 
  <email>vimal@javatpoint.com</email> 
]]>   
</employee>
```

Output:
```
<firstname>vimal</firstname>
<lastname>jaiswal</lastname>
<email>vimal@javatpoint.com</email>
```

### PCDATA
PCDATA: (Parsed Character Data): XML parsers are used to parse all the text in an XML document. PCDATA stands for Parsed Character data. PCDATA is the text that will be parsed by a parser. Tags inside the PCDATA will be treated as markup and entities will be expanded.

In other words you can say that a parsed character data means the XML parser examine the data and ensure that it doesn't content entity if it contains that will be replaced.

## XML Schema
- Known as XML Schema Definition (XSD)
- Defines the elements, attributes and data types
- Describes and validates the structure and the content of XML data

- An XML Schema describes the structure of an XML document
- An XML document with correct syntax is called "Well Formed".
- An XML document validated against an XML Schema is both "Well Formed" and "Valid".

### Definition Types
You can define XML schema elements in the following ways −

#### Simple Type
Simple type element is used only in the context of the text. Some of the predefined simple types are: `xs:integer, xs:boolean, xs:string, xs:date`. For example −

```xml
<xs:element name = "phone_number" type = "xs:int" />
```
#### Complex Type
A complex type is a container for other element definitions. This allows you to specify which child elements an element can contain and to provide some structure within your XML documents. For example −

```xml
<xs:element name = "Address">
   <xs:complexType>
      <xs:sequence>
         <xs:element name = "name" type = "xs:string" />
         <xs:element name = "company" type = "xs:string" />
         <xs:element name = "phone" type = "xs:int" /> 
      </xs:sequence> 
   </xs:complexType>
</xs:element> 
```
In the above example, Address element consists of child elements. This is a container for other `<xs:element>` definitions, that allows to build a simple hierarchy of elements in the XML document.

#### Global Types
With the global type, you can define a single type in your document, which can be used by all other references. For example, suppose you want to generalize the person and company for different addresses of the company. In such case, you can define a general type as follows −
```xml
<xs:element name = "AddressType">
   <xs:complexType>
      <xs:sequence>
         <xs:element name = "name" type = "xs:string" />
         <xs:element name = "company" type = "xs:string" />
      </xs:sequence> 
   </xs:complexType>
</xs:element> 
```
Now let us use this type in our example as follows −
```xml
<xs:element name = "Address1">
   <xs:complexType>
      <xs:sequence>
         <xs:element name = "address" type = "AddressType" />
         <xs:element name = "phone1" type = "xs:int" /> 
      </xs:sequence> 
   </xs:complexType>
</xs:element> 

<xs:element name = "Address2">
   <xs:complexType>
      <xs:sequence>
         <xs:element name = "address" type = "AddressType" />
         <xs:element name = "phone2" type = "xs:int" /> 
      </xs:sequence> 
   </xs:complexType>
</xs:element> 
```
Instead of having to define the name and the company twice (once for Address1 and once for Address2), we now have a single definition. This makes maintenance simpler, i.e., if you decide to add "Postcode" elements to the address, you need to add them at just one place.

### Attributes
Attributes in XSD provide extra information within an element. Attributes have name and type property as shown below −
```xml
<xs:attribute name = "x" type = "y"/>
```

### XSD Restrictions/Facets
Restrictions are used to define acceptable values for XML elements or attributes. Restrictions on XML elements are called facets.

#### Restrictions on Values
The following example defines an element called "age" with a restriction. The value of age cannot be lower than 0 or greater than 120:
```xml
<xs:element name="age">
  <xs:simpleType>
    <xs:restriction base="xs:integer">
      <xs:minInclusive value="0"/>
      <xs:maxInclusive value="120"/>
    </xs:restriction>
  </xs:simpleType>
</xs:element>
```

#### Restrictions on a Set of Values
```xml
<xs:element name="car">
  <xs:simpleType>
    <xs:restriction base="xs:string">
      <xs:enumeration value="Audi"/>
      <xs:enumeration value="Golf"/>
      <xs:enumeration value="BMW"/>
    </xs:restriction>
  </xs:simpleType>
</xs:element>
```
Above example defines an element called "car" with a restriction. The only acceptable values are: Audi, Golf, BMW

### Default and Fixed Values for Simple Elements
- Simple elements may have a default value OR a fixed value specified.
- A default value is automatically assigned to the element when no other value is specified.
- In the following example the default value is "red":
```xml
<xs:element name="color" type="xs:string" default="red"/>
```
- A fixed value is also automatically assigned to the element, and you cannot specify another value.
- In the following example the fixed value is "red":
```xml
<xs:element name="color" type="xs:string" fixed="red"/>
```

## DTD
- The XML Document Type Declaration, commonly known as DTD, is a way to describe XML language precisely. 
- DTDs check vocabulary and validity of the structure of XML documents against grammatical rules of appropriate XML language.
- An XML DTD can be either specified inside the document, or it can be kept in a separate document and then liked separately.
- An XML document with correct syntax is called `Well Formed`.
- An XML document validated against a DTD is both "Well Formed" and `Valid`.

### Syntax of DTD
```xml
<!DOCTYPE element DTD identifier
[
   declaration1
   declaration2
   ........
]>
```

- The DTD starts with `<!DOCTYPE` delimiter.
- An element tells the parser to parse the document from the specified root element.
- DTD identifier is an identifier for the document type definition, which may be the path to a file on the system or URL to a file on the internet. If the DTD is pointing to external path, it is called External Subset.
- The square brackets [ ] enclose an optional list of entity declarations called Internal Subset.

### Elements
In a DTD, elements are declared with an ELEMENT declaration.

#### Syntax
```xml
<!ELEMENT element-name category>
or
<!ELEMENT element-name (element-content)>
```

#### Empty Elements
```xml
<!ELEMENT element-name EMPTY>
```

#### Elements with Parsed Character Data
```xml
<!ELEMENT element-name (#PCDATA)>
```
Example:
```xml
<!ELEMENT from (#PCDATA)>
```

#### Elements with Children (sequences)
```xml
<!ELEMENT element-name (child1)>

<!ELEMENT element-name (child1,child2,...)>

<!ELEMENT note (to,from,heading,body)>
```

#### Example
```xml
<!ELEMENT note (to,from,heading,body)>
<!ELEMENT to (#PCDATA)>
<!ELEMENT from (#PCDATA)>
<!ELEMENT heading (#PCDATA)>
<!ELEMENT body (#PCDATA)>
```
#### Declaring Minimum One Occurrence (`+`)
```xml
<!ELEMENT element-name (child-name+)>
```
#### Declaring Zero or More Occurrences (`*`)
```xml
<!ELEMENT element-name (child-name*)>
```

#### Declaring Mixed Content
```xml
<!ELEMENT note (#PCDATA|to|from|header|message)*>
```

### Attributes
In a DTD, attributes are declared with an ATTLIST declaration.
#### Syntax
```xml
<!ATTLIST element-name attribute-name attribute-type attribute-value>
```
#### DTD example:
```xml
<!ATTLIST payment type CDATA "check">
```
#### XML example:
```xml
<payment type="check" />
```

#### attribute-value
`value` - The default value of the attribute
`#REQUIRED` -   The attribute is required
`#IMPLIED` - The attribute is optional
`FIXED` - The attribute value is fixed

#### attribute-type
`CDATA` - The value is character data
`(en1|en2|..)`  The value must be one from an enumerated list
`ID`  The value is a unique id
`IDREF` The value is the id of another element
`IDREFS`  The value is a list of other ids
`NMTOKEN` The value is a valid XML name
`NMTOKENS`  The value is a list of valid XML names
`ENTITY`  The value is an entity
`ENTITIES`  The value is a list of entities
`NOTATION`  The value is a name of a notation
`xml:`  The value is a predefined xml value

#### Example
- DTD:
```xml
<!ELEMENT square EMPTY>
<!ATTLIST square width CDATA "0">
```

- Valid XML:
```xml
<square width="100" />
```
In the example above, the "square" element is defined to be an empty element with a "width" attribute of  type CDATA. If no width is specified, it has a default value of 0.

### Internal DTD
A DTD is referred to as an internal DTD if elements are declared within the XML files. To refer it as internal DTD, standalone attribute in XML declaration must be set to yes. This means, the declaration works independent of an external source.

#### Syntax
Following is the syntax of internal DTD −

```xml
<!DOCTYPE root-element [element-declarations]>
```

Where `root-element` is the name of root element and element-declarations is where you declare the elements.

#### Example
```xml
<?xml version = "1.0" encoding = "UTF-8" standalone = "yes" ?>
<!DOCTYPE address [
   <!ELEMENT address (name,company,phone)>
   <!ELEMENT name (#PCDATA)>
   <!ELEMENT company (#PCDATA)>
   <!ELEMENT phone (#PCDATA)>
]>

<address>
   <name>Rohit Sharma</name>
   <company>Swastik Collge</company>
   <phone>9841000000</phone>
</address>
```

#### Rules
- The document type declaration must appear at the start of the document (preceded only by the XML header) − it is not permitted anywhere else within the document.
- Similar to the DOCTYPE declaration, the element declarations must start with an exclamation mark.
- The Name in the document type declaration must match the element type of the root element.

### External DTD
In external DTD elements are declared outside the XML file. They are accessed by specifying the system attributes which may be either the legal .dtd file or a valid URL. To refer it as external DTD, standalone attribute in the XML declaration must be set as no. This means, declaration includes information from the external source.

#### Syntax
Following is the syntax for external DTD −
```xml
<!DOCTYPE root-element SYSTEM "file-name">
```
Where file-name is the file with .dtd extension.

#### Example
```xml
<?xml version = "1.0" encoding = "UTF-8" standalone = "no" ?>
<!DOCTYPE address SYSTEM "address.dtd">
<address>
   <name>Rohit Sharma</name>
   <company>Swastik Collge</company>
   <phone>9841000000</phone>
</address>
```

The content of the DTD file `address.dtd` is as shown −
```xml
<!ELEMENT address (name,company,phone)>
<!ELEMENT name (#PCDATA)>
<!ELEMENT company (#PCDATA)>
<!ELEMENT phone (#PCDATA)>
```

### System Identifiers
A system identifier enables you to specify the location of an external file containing DTD declarations. Syntax is as follows −

`<!DOCTYPE name SYSTEM "address.dtd" [...]>`

As you can see, it contains keyword `SYSTEM` and a URI reference pointing to the location of the document.

### Public Identifiers
Public identifiers provide a mechanism to locate DTD resources and is written as follows −

`-<!DOCTYPE name PUBLIC "-//Beginning XML//DTD Address Example//EN">`

As you can see, it begins with keyword `PUBLIC`, followed by a specialized identifier. Public identifiers are used to identify an entry in a catalog. Public identifiers can follow any format, however, a commonly used format is called Formal Public Identifiers, or FPIs.

## When to Use a DTD/Schema?
- With a DTD, independent groups of people can agree to use a standard DTD for interchanging data.
- With a DTD, you can verify that the data you receive from the outside world is valid.
- You can also use a DTD to verify your own data.

## XPath
- XPath is an important and core component of XSLT standard. It is used to traverse the elements and attributes in an XML document.
- XPath is a W3C recommendation. XPath provides different types of expressions to retrieve relevant information from the XML document. It is syntax for defining parts of an XML document.

### Important features of XPath
- XPath defines structure: XPath is used to define the parts of an XML document i.e. element, attributes, text, namespace, processing-instruction, comment, and document nodes.
- XPath provides path expression: XPath provides powerful path expressions, select nodes, or list of nodes in XML documents.
- XPath is a core component of XSLT: XPath is a major element in XSLT standard and must be followed to work with XSLT documents.
- XPath is a standard function: XPath provides a rich library of standard functions to manipulate string values, numeric values, date and time comparison, node and QName manipulation, sequence manipulation, Boolean values etc.
- XPath is W3C recommendation.

### Nodes
XPath specifies seven types of nodes that can be output of the execution of the XPath expression.
- Root
- Element
- Text
- Attribute
- Comment
- Processing Instruction
- Namespace

```
Index   Expression    Description
1)      node-name     It is used to select all nodes with the given name "nodename"
2)      /             It specifies that selection starts from the root node.
3)      //            It specifies that selection starts from the current node that match the selection.
4)      .             Select the current node.
5)      ..            Select the parent of the current node.
6)      @             Selects attributes.
7)      student       Example - selects all nodes with the name `student`.
8)      class/student Example - selects all student elements that are children of class
9)      //student     Selects all student elements no matter where they are in the document
```

## XSLT
### XSL
XSL stands for EXtensible Stylesheet Language. It is similar to XML as CSS is to HTML. In case of HTML document, tags are predefined such as table, div, and span; and the browser knows how to add style to them and display those using CSS styles. But in case of XML documents, tags are not predefined. In order to understand and style an XML document, World Wide Web Consortium (W3C) developed XSL which can act as XML based Stylesheet Language. An XSL document specifies how a browser should render an XML document.

### What is XSLT ?
XSLT, Extensible Stylesheet Language Transformations, provides the ability to transform XML data from one format to another automatically.

An XSLT stylesheet is used to define the transformation rules to be applied on the target XML document. XSLT stylesheet is written in XML format. XSLT Processor takes the XSLT stylesheet and applies the transformation rules on the target XML document and then it generates a formatted document in the form of XML, HTML, or text format. This formatted document is then utilized by XSLT formatter to generate the actual output which is to be displayed to the end-user.

### Advantages
- Independent of programming. Transformations are written in a separate xsl file which is again an XML document.
- Output can be altered by simply modifying the transformations in xsl file. No need to change any code. So Web designers can edit the stylesheet and can see the change in the output quickly.

### XSLT Document Syntax

Syntax of .xsl file:

```xml
<?xml version = "1.0" encoding = "UTF-8"?>
<xsl:stylesheet version = "1.0" 
xmlns:xsl = "http://www.w3.org/1999/XSL/Transform">   
   <xsl:template match = "xpath"> 
      
      <!-- HTML tags 
      Used for formatting purpose. Processor will skip them and browser 
      will simply render them. 
      -->
      <xsl:for-each select="xpath">

        <xsl:value-of select = "xpath"/> 

      </xsl:for-each>
    </xsl:template>  
</xsl:stylesheet>
```

Now include/ink the xsl file into the XML

```xml
<?xml-stylesheet type = "text/xsl" href = "file.xsl"?>
```

`<?xml-stylesheet` tag is used to import the XSL file into the XML file with `type=text/xsl` and `href=file.xsl` attributes.


### Example
#### students.xsl
```xml
<?xml version = "1.0" encoding = "UTF-8"?>
<xsl:stylesheet version = "1.0" 
xmlns:xsl = "http://www.w3.org/1999/XSL/Transform">   
   <xsl:template match = "/"> 
      <html> 
         <body> 
            <h2>Students</h2> 
            <table border = "1"> 
               <tr bgcolor = "#9acd32"> 
                  <th>Roll No</th> 
                  <th>First Name</th> 
                  <th>Last Name</th> 
                  <th>Nick Name</th> 
                  <th>Marks</th> 
               </tr> 
               <xsl:for-each select="class/student"> 
               <!-- <xsl:sort select = "firstname"/>
               <xsl:if test = "marks > 90"> -->
                  <tr> 
                     <td> 
                        <xsl:value-of select = "@rollno"/> 
                     </td>
                     <td><xsl:value-of select = "firstname"/></td> 
                     <td><xsl:value-of select = "lastname"/></td> 
                     <td><xsl:value-of select = "nickname"/></td> 
                     <td><xsl:value-of select = "marks"/></td> 
                  </tr>
                  <!-- </xsl:if> --> 
               </xsl:for-each>
            </table> 
         </body> 
      </html> 
   </xsl:template>  
</xsl:stylesheet>
```

#### students.xml
```xml
<?xml version = "1.0"?>
<?xml-stylesheet type = "text/xsl" href = "students.xsl"?>
<class>
   <student rollno="393">
      <firstname>Ram</firstname> 
      <lastname>Sharma</lastname> 
      <nickname>Ram</nickname> 
      <marks>85</marks>
   </student> 
   <student rollno="493"> 
      <firstname>Rohit</firstname> 
      <lastname>Yadav</lastname> 
      <nickname>Rohit</nickname> 
      <marks>95</marks>
   </student>
   <student rollno="593"> 
      <firstname>Shishir</firstname> 
      <lastname>Gautam</lastname> 
      <nickname>Sisi</nickname> 
      <marks>90</marks> 
   </student> 
</class>
```

#### <xsl:template> 
Defines a way to reuse templates in order to generate the desired output for nodes of a particular type/context.

#### <xsl:value-of> 
Tag puts the value of the selected node as per XPath expression, as text.

#### <xsl:for-each> 
Tag applies a template repeatedly for each node.

#### <xsl:sort> 
Tag specifies a sort criteria on the nodes.

#### <message> 
Tag element helps to debug an XSLT processing. It is similar to javascript alerts. <xsl:> tag buffers a message to XSLT processor which terminates the processing and sends a message to the caller application to display the error message.
```xml
<xsl:if test = "firstname = ''"> 
   <xsl:message terminate = "yes">A first name field is empty. 
   </xsl:message> 
</xsl:if>
```

#### <xsl:choose> 
Tag specifies a multiple conditional tests against the content of nodes in conjunction with the <xsl:otherwise> and <xsl:when> elements.
```xml
<xsl:choose> 
 <xsl:when test = "marks > 90"> 
    High 
 </xsl:when> 

 <xsl:when test = "marks > 85"> 
    Medium 
 </xsl:when> 

 <xsl:otherwise> 
    Low 
 </xsl:otherwise> 
</xsl:choose> 
```

## DOM
- The Document Object Model (DOM) is the foundation of XML. XML documents have a hierarchy of informational units called nodes; DOM is a way of describing those nodes and the relationships between them.
- A DOM document is a collection of nodes or pieces of information organized in a hierarchy. This hierarchy allows a developer to navigate through the tree looking for specific information. Because it is based on a hierarchy of information, the DOM is said to be tree based.
- The XML DOM, on the other hand, also provides an API that allows a developer to add, edit, move, or remove nodes in the tree at any point in order to create an application.
- Understanding the DOM is a must for anyone working with HTML or XML.
- The XML DOM makes a tree-structure view for an XML document.
- We can access all elements through the DOM tree.
- We can modify or delete their content and also create new elements. The elements, their content (text and attributes) are all known as nodes.


`book.xml`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<bookstore>

  <book category="cooking">
    <title lang="en">Everyday Italian</title>
    <author>Giada De Laurentiis</author>
    <year>2005</year>
    <price>30.00</price>
  </book>

  <book category="children">
    <title lang="en">Harry Potter</title>
    <author>J K. Rowling</author>
    <year>2005</year>
    <price>29.99</price>
  </book>

</bookstore>
```

```javascript
txt = xmlDoc.getElementsByTagName("title")[0].childNodes[0].nodeValue;
```

And following `book.html` example loads a text string into an XML DOM object `book.xml`, and extracts the info from it with JavaScript:

```html
<!DOCTYPE html>
<html>
<body>

<p id="demo"></p>

<script>
var xhttp = new XMLHttpRequest();
xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      var xmlDoc = this.responseXML;
      var p = document.getElementById("demo");
      var titles = xmlDoc.getElementsByTagName("title");
      var titlesHtml = '<ul>';
      for(var i = 0; i < titles.length; i++){
            var cat = titles[i].parentNode.getAttribute('category');
        titlesHtml += "<li>" + titles[i].childNodes[0].nodeValue + " (" + cat +")</li>";
      }
        titlesHtml += '</ul>';
      p.innerHTML = titlesHtml;
    }
};
xhttp.open("GET", "book.xml", true);
xhttp.send();

function myFunction(xml) {
    var xmlDoc = xml.responseXML;
    document.getElementById("demo").innerHTML =
    xmlDoc.getElementsByTagName("title")[0].childNodes[0].nodeValue;
}
</script>

</body>
</html>
```

### DOM Parser
#### Parsing XML Text String
- The XML DOM (Document Object Model) defines the properties and methods for accessing and editing XML.
- However, before an XML document can be accessed, it must be loaded into an XML DOM object.
- All modern browsers have a built-in XML parser that can convert text into an XML DOM object.

This example parses a text string into an XML DOM object, and extracts the info from it with JavaScript:

`load_string.html`
```html
<html>
<body>

<p id="demo"></p>

<script>
var text, parser, xmlDoc;

text = "<bookstore><book>" +
"<title>Everyday Italian</title>" +
"<author>Giada De Laurentiis</author>" +
"<year>2005</year>" +
"</book></bookstore>";

parser = new DOMParser();
xmlDoc = parser.parseFromString(text,"text/xml");

document.getElementById("demo").innerHTML =
xmlDoc.getElementsByTagName("title")[0].childNodes[0].nodeValue;
</script>

</body>
</html>
```

### XML DOM Properties
These are some typical DOM properties:

- x.nodeName - the name of x
- x.nodeValue - the value of x
- x.parentNode - the parent node of x
- x.childNodes - the child nodes of x
- x.attributes - the attributes nodes of x

### XML DOM Methods
- x.getElementsByTagName(name) - get all elements with a specified tag name
- x.appendChild(node) - insert a child node to x
- x.removeChild(node) - remove a child node from x

`Note: In the list above, x is a node object.`

### Nodes
- Text is Always Stored in Text Nodes
- The XML DOM views an XML document as a tree-structure. The tree structure is called a node-tree.

### Node Parents, Children, and Siblings
- In a node tree, the top node is called the `root`
- Every node, except the root, has exactly one `parent node`
- A node can have any number of `children`
- A leaf is a node with `no children`
- `Siblings` are nodes with the same parent

### XML DOM Get Node Values
- The `nodeValue` property is used to get the text value of a node.
- The `getAttribute('attribute_name')` method returns the value of an attribute.
```javascript
x = xmlDoc.getElementsByTagName("title")[0];
txt = x.getAttribute("lang");
```

### Create a node
```javascript
newElement = xmlDoc.createElement("edition");
```

### Add a Node - appendChild()
```javascript
newEle = xmlDoc.createElement("edition");
xmlDoc.getElementsByTagName("book")[0].appendChild(newEle);
```

## XQuery
XQuery is a standardized language for combining documents, databases, Web pages and almost anything else. It is very widely implemented. It is powerful and easy to learn. XQuery is replacing proprietary middleware languages and Web Application development languages. XQuery is replacing complex Java or C++ programs with a few lines of code. XQuery is simpler to work with and easier to maintain than many other alternatives.

- **Functional Language** − XQuery is a language to retrieve/querying XML based data.
- **Analogous to SQL** − XQuery is to XML what SQL is to databases.
- **XPath based** − XQuery uses XPath expressions to navigate through XML documents.
- **Universally accepted** − XQuery is supported by all major databases.
- **W3C Standard** − XQuery is a W3C standard.

### Characteristics
- Functional Language − XQuery is a language to retrieve/querying XML based data.
- Analogous to SQL − XQuery is to XML what SQL is to databases.
- XPath based − XQuery uses XPath expressions to navigate through XML documents.
- Universally accepted − XQuery is supported by all major databases.
- W3C Standard − XQuery is a W3C standard.

### Benefits of XQuery
- Using XQuery, both hierarchical and tabular data can be retrieved.
- XQuery can be used to query tree and graphical structures.
- XQuery can be directly used to query webpages.
- XQuery can be directly used to build webpages.
- XQuery can be used to transform xml documents.
- XQuery is ideal for XML-based databases and object-based databases. Object databases are much more flexible and powerful than purely tabular databases.

## SAX
**SAX (Simple API for XML)** is an event-driven online algorithm for parsing XML documents, with an API developed by the XML-DEV mailing list. SAX provides a mechanism for reading data from an XML document that is an alternative to that provided by the Document Object Model (DOM). Where the DOM operates on the document as a whole, i.e. building the full Abstract  of XML document for convenience of the user, SAX parsers operate on each piece of the XML document sequentially, issuing parsing events while making single pass through the input stream.

XML-SAX initiates a SAX parse for an XML document. The XML-SAX operation code begins by calling an XML parser which begins to parse the document. When an event occurs such as the parser finding the start of an element, finding an attribute name, finding the end of an element and so on, the parser calls the handling procedure handlerProc with parameters describing the event. When the handling procedure returns, the parser continues to parse until it finds the next event and calls the handling procedure again. When the parser has finished parsing the document, control passes to the statement following the XML-SAX operation.

SAX parser has used to parse the xml file and better for memory management than sample xml parser and DOM. It does not keep any data in memory so it can be used for very large files. Following example will show how to get data from xml by using SAX API.

### XML Processing with SAX
A parser that implements SAX (i.e., a SAX Parser) functions as a stream parser, with an event-driven API.[1] The user defines a number of callback methods that will be called when events occur during parsing. The SAX events include (among others):

- XML Text nodes
- XML Element Starts and Ends
- XML Processing Instructions
- XML Comments

### Example
Given the following XML document:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<DocumentElement param="value">
     <FirstElement>
         &#xb6; Some Text
     </FirstElement>
     <?some_pi some_attr="some_value"?>
     <SecondElement param2="something">
         Pre-Text <Inline>Inlined text</Inline> Post-text.
     </SecondElement>
</DocumentElement>
```

This XML document, when passed through a SAX parser, will generate a sequence of events like the following:

- XML Element start, named DocumentElement, with an attribute param equal to "value"
- XML Element start, named FirstElement
- XML Text node, with data equal to "&#xb6; Some Text" (note: certain white spaces can be changed)
- XML Element end, named FirstElement
- Processing Instruction event, with the target some_pi and data some_attr="some_value" (the content after the target is just text; however, it is very common to imitate the syntax of XML attributes, as in this example)
- XML Element start, named SecondElement, with an attribute param2 equal to "something"
- XML Text node, with data equal to "Pre-Text"
- XML Element start, named Inline
- XML Text node, with data equal to "Inlined text"
- XML Element end, named Inline
- XML Text node, with data equal to "Post-text."
- XML Element end, named SecondElement
- XML Element end, named DocumentElement

### Parsing XML Using PHP
SAX parser has used to parse the xml file and better for memory management than sample xml parser and DOM. It does not keep any data in memory so it can be used for very large files. Following example will show how to get data from xml by using SAX API.

#### Example
`SAX.xml`
```xml
<?xml version = "1.0" encoding = "utf-8"?>
<tutors>
   <course>
      <name>Android</name>
      <country>Nepal</country>
      <email>contact@swastikcollege.edu.np</email>
   </course>
   <course>
      <name>Java</name>
      <country>Nepal</country>
      <email>contact@swastikcollege.edu.np</email>
   </course>
</tutors>
```
`sax-parser.php`
```php
<?php
   //Reading XML using the SAX(Simple API for XML) parser 
   
   $tutors   = array();
   $elements   = null;
   
   // Called to this function when tags are opened 
   function startElements($parser, $name, $attrs) {
      global $tutors, $elements;
      
      if(!empty($name)) {
         if ($name == 'COURSE') {
            // creating an array to store information
            $tutors []= array();
         }
         $elements = $name;
      }
   }
   
   // Called to this function when tags are closed 
   function endElements($parser, $name) {
      global $elements;
      
      if(!empty($name)) {
         $elements = null;
      }
   }
   
   // Called on the text between the start and end of the tags
   function characterData($parser, $data) {
      global $tutors, $elements;
      
      if(!empty($data)) {
         if ($elements == 'NAME' || $elements == 'COUNTRY' ||  $elements == 'EMAIL' ||  $elements == 'PHONE') {
            $tutors[count($tutors)-1][$elements] = trim($data);
         }
      }
   }
   
   // Creates a new XML parser and returns a resource handle referencing it to be used by the other XML functions. 
   $parser = xml_parser_create(); 
   
   xml_set_element_handler($parser, "startElements", "endElements");
   xml_set_character_data_handler($parser, "characterData");
   
   // open xml file
   if (!($handle = fopen('sax.xml', "r"))) {
      die("could not open XML input");
   }
   
   while($data = fread($handle, 4096)) // read xml file {
      xml_parse($parser, $data);  // start parsing an xml document 
   }
   
   xml_parser_free($parser); // deletes the parser
   $i = 1;
   
   foreach($tutors as $course) {
      echo "course No - ".$i.'<br/>';
      echo "course Name - ".$course['NAME'].'<br/>';
      echo "Country - ".$course['COUNTRY'].'<br/>';
      echo "Email - ".$course['EMAIL'].'<br/>';
      echo "Phone - ".$course['PHONE'].'<hr/>'; 
      $i++; 
   }
?>
```
