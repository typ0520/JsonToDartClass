[![GitHub stars](https://img.shields.io/github/stars/typ0520/JsonToDartClass.svg?style=social&label=Stars&style=plastic)](https://github.com/typ0520/JsonToDartClass/stargazers)
[![JetBrains Plugin Download](https://img.shields.io/jetbrains/plugin/d/10013-fastdex-plugin-.svg)](https://plugins.jetbrains.com/plugin/9960-JsonToDartClass)
[![license](https://img.shields.io/github/license/typ0520/JsonToDartClass.svg)](https://github.com/typ0520/JsonToDartClass/blob/master/LICENSE)

[![Dart](https://img.shields.io/badge/%20language-Flutter-red.svg)](https://flutter.dev/)
[![IntelliJ Idea Plugin](https://img.shields.io/badge/plugin-IntelliJ%20%20Idea-blue.svg)](https://plugins.jetbrains.com/plugin/9960-JsonToDartClass)
[![Android Studio Plugin](https://img.shields.io/badge/plugin-AndroidStudio-green.svg)](https://plugins.jetbrains.com/plugin/9960-JsonToDartClass)

# JsonToDartClass

Hi, Welcome! This is a plugin to generate Dart `model class` from JSON string, in another word, a plugin that converts JSON string to Dart `model class` (Json to Dart)

### Overview

This is a very cool tool for Flutter developers, it can convert a JSON string to Dart `model class`. The tool could not only recognize the primitive types but also auto create complex types. It's easily accessible, we provide shortcut keymap `ALT + K` for Windows and `Option + K` for Mac, have a try and you'll fall in love with it! JsonToDartClass just makes programming more enjoyable, enjoy coding!

### Easy Use
![alt text](https://plugins.jetbrains.com/files/12737/screenshot_20027.png)

### Usage
* Search 'JsonToDartClass' in Intellij Idea Plugin Repository Or AndroidStudio Plugin Repository And Install it.

> File --> Settings --> Plugins --> Browse Repositories --> Search JsonToDartClass

* Restart your IDE

* Press `ALT + K` for Windows or `Option + K` for Mac or right click on package -> `New`->`Dart class file from JSON` and continue as guided.

### Advanced usage
Have a try with the advanced dialog :stuck_out_tongue_winking_eye:

### Features
* Generating Dart data class from any legal JSON string or any **URLs that returns a JSON string as response** or **local file that contains JSON string**
* Generating Dart data class from any legal JSON text when right click on directory and select `New` -> `Dart class File from JSON`
* Formatting any legal JSON string

### Generate Example
This is the example JSON from json.org


```json
{
    "glossary":{
        "title":"example glossary",
        "GlossDiv":{
            "title":"S",
            "GlossList":{
                "GlossEntry":{
                    "ID":"SGML",
                    "SortAs":"SGML",
                    "GlossTerm":"Standard Generalized Markup Language",
                    "Acronym":"SGML",
                    "Abbrev":"ISO 8879:1986",
                    "GlossDef":{
                        "para":"A meta-markup language, used to create markup languages such as DocBook.",
                        "GlossSeeAlso":[
                            "GML",
                            "XML"
                        ]
                    },
                    "GlossSee":"markup"
                }
            }
        }
    }
}
```
And with this plugin converting, Dart classes would generate like this by default

```dart
class Example {
    Glossary glossary;

    Example({this.glossary});

    factory Example.fromJson(Map<String, dynamic> json) {
        return Example(
            glossary: json['glossary'] != null ? Glossary.fromJson(json['glossary']) : null,
        );
    }

    Map<String, dynamic> toJson() {
        final Map<String, dynamic> data = new Map<String, dynamic>();
        if (this.glossary != null) {
            data['glossary'] = this.glossary.toJson();
        }
        return data;
    }
}

class Glossary {
    GlossDiv glossDiv;
    String title;

    Glossary({this.glossDiv, this.title});

    factory Glossary.fromJson(Map<String, dynamic> json) {
        return Glossary(
            glossDiv: json['glossDiv'] != null ? GlossDiv.fromJson(json['glossDiv']) : null,
            title: json['title'],
        );
    }

    Map<String, dynamic> toJson() {
        final Map<String, dynamic> data = new Map<String, dynamic>();
        data['title'] = this.title;
        if (this.glossDiv != null) {
            data['glossDiv'] = this.glossDiv.toJson();
        }
        return data;
    }
}

class GlossDiv {
    GlossList glossList;
    String title;

    GlossDiv({this.glossList, this.title});

    factory GlossDiv.fromJson(Map<String, dynamic> json) {
        return GlossDiv(
            glossList: json['glossList'] != null ? GlossList.fromJson(json['glossList']) : null,
            title: json['title'],
        );
    }

    Map<String, dynamic> toJson() {
        final Map<String, dynamic> data = new Map<String, dynamic>();
        data['title'] = this.title;
        if (this.glossList != null) {
            data['glossList'] = this.glossList.toJson();
        }
        return data;
    }
}

class GlossList {
    GlossEntry glossEntry;

    GlossList({this.glossEntry});

    factory GlossList.fromJson(Map<String, dynamic> json) {
        return GlossList(
            glossEntry: json['glossEntry'] != null ? GlossEntry.fromJson(json['glossEntry']) : null,
        );
    }

    Map<String, dynamic> toJson() {
        final Map<String, dynamic> data = new Map<String, dynamic>();
        if (this.glossEntry != null) {
            data['glossEntry'] = this.glossEntry.toJson();
        }
        return data;
    }
}

class GlossEntry {
    String abbrev;
    String acronym;
    GlossDef glossDef;
    String glossSee;
    String glossTerm;
    String iD;
    String sortAs;

    GlossEntry({this.abbrev, this.acronym, this.glossDef, this.glossSee, this.glossTerm, this.iD, this.sortAs});

    factory GlossEntry.fromJson(Map<String, dynamic> json) {
        return GlossEntry(
            abbrev: json['abbrev'],
            acronym: json['acronym'],
            glossDef: json['glossDef'] != null ? GlossDef.fromJson(json['glossDef']) : null,
            glossSee: json['glossSee'],
            glossTerm: json['glossTerm'],
            iD: json['iD'],
            sortAs: json['sortAs'],
        );
    }

    Map<String, dynamic> toJson() {
        final Map<String, dynamic> data = new Map<String, dynamic>();
        data['abbrev'] = this.abbrev;
        data['acronym'] = this.acronym;
        data['glossSee'] = this.glossSee;
        data['glossTerm'] = this.glossTerm;
        data['iD'] = this.iD;
        data['sortAs'] = this.sortAs;
        if (this.glossDef != null) {
            data['glossDef'] = this.glossDef.toJson();
        }
        return data;
    }
}

class GlossDef {
    List<String> glossSeeAlso;
    String para;

    GlossDef({this.glossSeeAlso, this.para});

    factory GlossDef.fromJson(Map<String, dynamic> json) {
        return GlossDef(
            glossSeeAlso: json['glossSeeAlso'] != null ? new List<String>.from(json['glossSeeAlso']) : null,
            para: json['para'],
        );
    }

    Map<String, dynamic> toJson() {
        final Map<String, dynamic> data = new Map<String, dynamic>();
        data['para'] = this.para;
        if (this.glossSeeAlso != null) {
            data['glossSeeAlso'] = this.glossSeeAlso;
        }
        return data;
    }
}
```

### Build From Source

Want to try out the newest features?

```shell
$ git clone https://github.com/typ0520/JsonToDartClass
$ cd JsonToDartClass
$ ./gradlew buildPlugin
```

And you're done! Go to directory `build/distributions` and you'll find `JsonToDartClass-x.x.zip`, which can be installed via **Install plugin from disk...**.

### Contribute to This Repo

Find it useful and want to contribute? All sorts of contributions are welcome, including but not limited to:

- Open an issue [here](https://github.com/typ0520/JsonToDartClass/issues) if you find a bug;

- Help test the EAP version and report bugs:

Go to the "Plugins" settings, click "Browse repositories..." => "Manage repositories..." and click the "+" button to add the EAP channel repository URL "https://plugins.jetbrains.com/plugins/eap/list". Optionally, you can also add the Alpha and Beta channel repository URLs "https://plugins.jetbrains.com/plugins/alpha/list" and "https://plugins.jetbrains.com/plugins/beta/list".

> Kindly note that the "EAP" or "Alpha" or "Beta" channel update may be unstable and tend to be buggy, if you want to get back to the stable version, remove the "EAP" or "Alpha" or "Beta" version and reinstall this plugin from the "JetBrains Plugin Repository" channel, which can be filtered by the drop-down menu next to the search input field.

- Contribute your code:

```shell
$ git clone https://github.com/typ0520/JsonToDartClass
$ cd JsonToDartClass
```

Open the `build.gradle` in IntelliJ, open "Gradle" tool window, expand the project view to "JsonToDartClass | Tasks | intellij | runIde", right-click and choose "Debug ...", and you're done! Create your PR [here](https://github.com/typ0520/JsonToDartClass/pulls)!

### Others
* Any kind of issues are welcome.
* Pull Requests are highly appreciated.

### Find it useful ? :heart:
* Support and encourage me by clicking the :star: button on the upper right of this page. :v:
* Share to others to help more people have a better develope expierience :heart:

### Thanks
* [@JsonToKotlinClass](https://github.com/wuseal/JsonToKotlinClass) Most of the code comes from this library
