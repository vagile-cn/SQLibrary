Version 7.1 (release)
- Built on Bukkit 1.12.2-R0.1-SNAPSHOT
- Change mysql-connector-java version to 5.1.45
- Add useSSL=false to mysql jdbc connection string

Version 7.0 (release)
- Built on Bukkit 1.7.4-R0.2.
- Removed bad design pattern and replaced with hierarchy (one of the original reasons for forking this library).
- Renamed writeError() and writeInfo() to info(), warning(), and error(). Backwards compatibility retained.
- Moved README to correct location for GitHub.
- No connection pooling as was planned for this version.
- The super secret surprise and one of the reasons SQLibrary must be a jar dependency, also not in this version.
- Released 7.0 (2013-12-29).

Version 6.1 (release)
- Built on Bukkit 1.6.2-R1.0.
- Added support for Spout.
- Released 6.1 (2013-10-15).

Version 6.0 (alpha)
- Use first development build for 1.6.1.
- SQLibrary's major version now corresponds to Minecraft.
- Databases no longer require a username or password (use one less parameter for each or empty strings).
- Added two new constructors to each database for empty passwords and empty usernames.
- Fixed shorthand Oracle constructor still containing a port parameter.
- Fixed SQLite constructor identifying itself as H2 (https://github.com/PatPeter/SQLibrary/issues/12).
- Added insert(PreparedStatement ps).
- Released 6.0 (2013-07-08).

Version 4.2 (release)
- Readded MySQL(Logger, String, String, String, String, String, String) as a deprecated constructor.
- Fixed improper usage of database delegates and added usage of FilenameDatabase.
- Expanded FilenameDatabase to support custom extensions, and subsequently SQLite and H2.
- Deleted SQLTestSuite for being extremely outdated and no longer useful as an educational tool.
- TimeClock will be the official SQLibrary example plugin when it is finished.

Version 4.1 (release)
- In 4.0, MySQL(Logger, String, String, String, String, String, String) was changed to MySQL(Logger, String, String, int, String, String, String).
- In 4.0, SQLite(Logger logger, String name, String location) was changed to SQLite(Logger logger, String directory, String filename).
- In 4.0, wipeTable() was changed to truncate().
- In 4.0, checkTable() was changed to isTable().
- In 4.0, createTable(), checkTable(), and wipeTable() were deprecated.
- checkConnection() is no longer a pointless null check.
- checkConnection() changed to isOpen() and isOpen(int timeout).
- checkConnection() is now deprecated.
- isTable() in SQLite restored to previous algorithm - was always returning true (https://github.com/PatPeter/SQLibrary/issues/4).
- insert() added to Database that returns an ArrayList<Long> of generated keys (https://github.com/PatPeter/SQLibrary/issues/5).
- Removed Ovrimos - no JDBC connector available.
- Laid groundwork for downloading and installing JDBC connectors for all supported DBMS.

Version 4.0 (release)
- Added support for 13 more DBMSs: Firebird, FrontBase, DB2, H2, Informix, Ingres, MaxDB, MicrosoftSQL, Mongo, mSQL, Oracle, Ovrimos, and PostgreSQL.
- query() method optimization.
- query() will no longer return null. Instead, it will return a ResultSet containing the number of changes by statements that do not return a ResultSet.
- query() compatibility with PreparedStatements and Builders added.
- Database and DatabaseConfig no longer use separate enumerations to represent the supported databases.
- Encapsulation of StatementEnums for each Database.
- Finished Statements enumeration for MySQL, SQLite, H2, MicrosoftSQL, PostgreSQL, and Oracle.
- getStatement() is now public.
- Added many null and empty String checks as (Runtime) DatabaseExceptions.
- Deprecation and renaming of several methods.
- Database objects now use delegates to provide get methods, but have remained immutable with private set methods.
- Addition of a functional SELECT statement builder for MySQL.

Version 3.5 (release)
- Implemented initialize() and open() for every database driver except H2.
- Added internal variable driver for Builder checks.
- Created a package for the Factory classes and a package for the query Builders.
- Renamed MySQLTable to simply Table.
- Added classes Select, Insert, and Update.
- Database abstract methods are now public for better usage in multi-database plugins.
- open() now returns a boolean instead of a Connection. Use getConnection() if necessary.
- Added query(PreparedStatement ps) as an abstract function so that the query() shortcuts and validation can be used with PreparedStatements.
- Made getStatement() an abstract function so that it is no longer breaks the rules of inheritance.
- Since open() now returns a boolean for error checking, there is no point in using SQLException.
- Moved Statements to each child class.
- Created SQLStatement interface to enforce getStatement() in child classes.
- Only source released.

Version 3.1 (release)
- Added support for every statement in MySQL and SQLite into their respective query() methods.
- All boolean methods return false on fail, all other methods throw exceptions so that plugin authors can check for errors.
- Moved close(), getConnection(), checkConnection(), and prepare() into Database.java.
- Actually implemented the prefix() method.
- Released 3.1 (2012-09-09).

Version 3.0.8 (alpha)
- Fixed IndexOutOfBoundsException in getStatement() (https://github.com/PatPeter/SQLibrary/issues/2).
- Added DatabaseException to getStatement() and MySQL.
- Updated the Test Suite to 1.2 and added DatabaseException to SQLite.
- query() now throws DatabaseException so that plugins can know whether a query failed or not.
- Never released.

Version 3.0.7 (alpha)
- Created plugin.yml for exporting jar files.
- Merged Belphemur's code in with the Library's main code.
- Fixed DatabaseFactory returning DatabaseHandler and InvalidConfiguration using an inappropriate super().
- Specified method names in error messages for easier debugging.
- Changed executeQuery() to executeUpdate() in query() for SQLite.
- Added lastUpdate to Database for any executeUpdate() queries.
- Added INSERT, UPDATE, and DELETE to query() switches.
- Added the rest of standard statements to switches.
- Added many more statements for MySQL and SQLite to Database.Statements.
- Released 3.0.7 (2012-03-17).

Version 3.0.6 (alpha)
- Added a Factory (https://github.com/PatPeter/SQLibrary/pull/1).
- Fixed "Too many connections" propagated from faulty Linux fix.
- Renamed DatabaseHandler.java to simply Database.java.
- Removed imports in Oracle.java until developed.
- Merged Test Suite with library in GitHub.
- Removed infinite loop in SQLite and the original retry().
- Merged CHANGELOG with README.
- Added SQLibrary.java on jertocvil's request.
- Released 3.0.6 (2012-03-11).

Version 3.0.5.2 (alpha-fix)
- Class only uses one connection to avoid "Too Many Connections".

Version 3.0.5.1 (alpha-fix)
- Removed .replace("_","\\_") from variables.
- Fixed checkConnection() based on Feed_Dante's analysis.
- Attempted yet another fix to query() saying it does not return a ResultSet.

Version 3.0.5 (alpha)
- Made MySQL getConnection() reopen the connection with open() every time.
- Added support for underscores in hostnames, databases, and usernames by escaping them.
- Added prepare().
- Removed this.connection and converted all instances to local variables.
- Added empty class files for future database support.
- Fixed getStatement() by changing equals() to equalsIgnoreCase().
- Fixed query() by having it return result instead of null.
- Removed redundant exceptions from methods.
- Released 3.0.5 (2011-09-17).

Version 3.0.4 (alpha)
- Moved writeInfo and writeError into superclass.
- Moved retry and retryResult back into SQLite.
- Fixed error where query() could only run SELECT statements by adding an enum and test method.
- Added initialize() method that checks for the library.
- Connection defaults to null in superclass.
- Methods always reference this.connection.
- Fixed createTable() wrongly checking for null strings.
- Added getStatement() method that determines what statement the user is calling.

Version 3.0.3.2 (alpha, fix)
- Added port number to the MySQL constructor and class.
- Added default values for hostname, port number, and database.

Version 3.0.3.1 (alpha, fix)
- Attempted fix for 68x's bug: http://forums.bukkit.org/threads/lib-tut-mysql-sqlite-bukkit-drivers.33849/#post-629713 . Added "/" to the end of the jdbc: url.

Version 3.0.3 (alpha)
- Added constructor to DatabaseHandler for use of super() in subclasses.
- Added DATABASE_PREFIX to DatabaseHandler.

Version 3.0.2 (alpha)
- Changed top level of package from 'com' to 'lib', which makes much more sense. Do not "Link to files and recreate folder structure with virtual folders", it will not allow you to add other libraries with the same top level.
- Added Javadoc for all methods.
- Fixed several typos.
- Removed redundant methods retry() and retryResult().
- Created empty Oracle driver to finish later and as an example for anyone wishing to add more drivers (Microsoft SQL, PostgreSQL, etc.).

Version 3.0.1 (alpha)
- Changed developer from alta189 to PatPeter.
- Consolidated two packages (MySQL and SQLLite) into one.
- Converted DatabaseHandler.java into an abstract class so that additional database engines can be supported.
- Removed redundant methods (methods pointing to a method in another file with no changes or methods that change very minor aspects of code in other methods).
- Changed all *Query methods to simply query().

Version 2.0
- Added MySQL support.
- New Structure.
- Need to update tutorial.
- New Example plugin.

Version 1.2
- Added checkTable(String table) - will return true/false.

Version 1.1
- Added insertQuery(String query) - Use this when inserting data to a table! In the tutorial I use querySQL(String query) please use this instead!!!!

Version 1.0
- Release.
