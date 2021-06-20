# AndroidTesting
- It Contains all the test cases including unit test and ui test
- There are 3 types of tesging in android
    - Unit test - It covers around 70%
    - Integration test - It covers 20%
    - UI test - It covers 10%

## Unit testing
- A unit test verifies in isolation the functionality of a certain component. For example, assume a button in an Android activity is used to start another activity. A unit test would determine, if the corresponding intent was issued, not if the second activity was started
- A unit tests for an Android application can be:
- **local unit test** - which runs on the JVM
- **Android unit test** - which runs on the Android runtime
- If they run on the JVM, they are executed against a modified version of the android.jar Android library. In this version all final modifiers have been stripped off. This makes it easier to use mocking libraries, like Mockito.
- The local unit tests of an Android project should be located in the app/src/test folder.
- For unit testing we require any of these 2 libraries 1.JUnit,Mockito 2. RoboElectric
-   ```
        testImplementation 'junit:junit:4.13.2'
        testImplementation 'org.mockito:mockito-core:2.21.0'
    ```
## Advantage Of Unit  testing
- Helps in finding bugs early.
- As it helps to find the bugs in the early stage of development and reduces the development cost and time.
- Simplifies refactoring and provides documentation.
## Google Truth
- But with JUnit we will use Google Truth, to simplify the assertions. As it is not available by default; we need to add it inside the dependency block of app level build.gradle file.
-   ```
        testImplementation "com.google.truth:truth:1.1.2"
    ```
- **@Test:** @Test is an annotation provided by JUnit Framework for marking a method as a test case. As you can see here, each method is a test case testing the input field for a possible input. This instructs the compiler to consider the method as a test case in the test suit.
- **assertTrue():** assertTrue is a method provided by Junit Framework to assert (force) the value inside it’s parentheses as TRUE. If the value inside the parentheses evaluates to be false, the test case fails.
- **assertFalse():** Same as the assertTrue method except that it asserts the argument inside the parentheses to be false instead of true. If the passed parameter is true, the test case fails.
```
import static org.junit.Assert.assertFalse;
import static org.junit.Assert.assertTrue;
/**
 * Unit tests for the EmailValidator logic.
 */
public class EmailValidatorTest {
    @Test
    public void emailValidator_CorrectEmailSimple_ReturnsTrue() {
        assertTrue(EmailValidator.isValidEmail("name@email.com"));
    }
    @Test
    public void emailValidator_CorrectEmailSubDomain_ReturnsTrue() {
        assertTrue(EmailValidator.isValidEmail("name@email.co.uk"));
    }
    @Test
    public void emailValidator_InvalidEmailNoTld_ReturnsFalse() {
        assertFalse(EmailValidator.isValidEmail("name@email"));
    }
    @Test
    public void emailValidator_InvalidEmailDoubleDot_ReturnsFalse() {
        assertFalse(EmailValidator.isValidEmail("name@email..com"));
    }
    @Test
    public void emailValidator_InvalidEmailNoUsername_ReturnsFalse() {
        assertFalse(EmailValidator.isValidEmail("@email.com"));
    }
    @Test
    public void emailValidator_EmptyString_ReturnsFalse() {
        assertFalse(EmailValidator.isValidEmail(""));
    }
    @Test
    public void emailValidator_NullEmail_ReturnsFalse() {
        assertFalse(EmailValidator.isValidEmail(null));
    }
}
```
Junit: It is a “Unit Testing” framework for Java Applications. It is an automation framework for Unit as well as UI Testing. It contains annotations such as @Test, @Before, @After etc.
Mockito: Mockito mocks (or fakes) the dependencies required by the class being tested. It provides annotations such as @Mock.