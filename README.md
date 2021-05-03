# XML Schema for MuJoCo Files
This project is a **XML schema for validation of MJCF files**. It relies on the use of XSD files and is relevant for MuJoCo 2.0 . 

## What does MJCF mean?
**MJCF** (namely *MuJoCo's XML modeling format*) is MuJoCo's native XML file format for describing models. It is an alternative to the more common **URDF** format.

For more details about MuJoCo and why MJCF format should be preferred to URDF using that library, see [*1.*](#references) .

## Why should I use XSD validation?
XSD validation eases the writing of XML file, and can significantly improve your development efficiency. Basically, when a XSD validator is linked with a given XML file, that XSD file will check that that XML file respects the syntax it defines.

More concretely, XSD validation allows (among other things) **autocompletion** of elements and attributes, **type checking** of attributes as well as **validation of nesting rules** between elements.

For more details about the (almost unlimited) power of XSD validation, see [*2.*](#references)

## Installation
Simply `git clone` the project to a convenient place (for example nearby the folder where MuJoCo is installed).

*NB: One recommends **not to modify the structure** of the project. If you decide to do so, you will have to adapt import paths (see **Project Structure** paragraph below for further information).*

## Usage
The `mujoco.xsd` file is the main file of the project. Therefore, it is the only file you need to link with your MJCF files so as to allow validation.

There are **several ways** to link a XSD validator to a given XML file, see for example [*3.*](#references) .

Usually, a **simple way** is to add the following tag at the beginning of your MJCF-XML files:
>`<?xml-model href="relative/path/to/mujoco.xsd"?>`

*NB: Most of XML plugins also allow to enable XSD validation for a whole directory/project **without additional tag**. Therefore, if you use such a plugin, you are strongly encouraged to check its documentation!*

## Project Structure
The organisation of this project is mapped to MJCF syntax. To access complete MJCF syntax documentation, see [*4.*](#references) .

### Typology of files
As mentionned before, the main file of the project is `mujoco.xsd` . It is located at the root of the project. It defines the **relationships between elements** of the MJCF syntax.

The attributes of elements are not defined in `mujoco.xsd`: they are imported from files located in the `element_types` folder. Each direct child of the `<mujoco>` root element has got its own file. For example, the `<asset>` element has got its `element_types/asset.xsd` file.

Each attribute is typed. So as to pool the defintion of types, all attribute types are located in the `attribute_types/attribute_types.xsd` file. At the head of that file, all shared types are stacked.

### Naming convention of types
The type corresponding to the element/attribute **X** is by convention named **XType**.

In case of ambiguity, one can concatenate the name of the parent **Y**, so that it becomes **YXType**.

## Potential improvements
This project was originally written by a XSD validation noob, so it would be cool if you can **help to improve it**!

Don't hesitate to **report issues** or **open your own PRs**!

Some potential improvements I foresee:
- Fixing typos and reporting errors
- Improve attribute typing, especially when it comes to sequences of `float`/`int`.
- This ReadMe was not written by a native English speaker, so it is probably full of mistakes...

## References
1. MuJoCo - Overview: http://www.mujoco.org/book/index.html
4. W3C - XSD Documentation: https://www.w3.org/TR/xmlschema11-1/
2. RedHat XML - Validation: https://github.com/redhat-developer/vscode-xml/blob/master/docs/Validation.md
3. MuJoCo - XML Reference: http://www.mujoco.org/book/XMLreference.html

## Contributors
- [ronansgd](https://github.com/ronansgd) :fr:

## License
[MIT](https://choosealicense.com/licenses/mit/)